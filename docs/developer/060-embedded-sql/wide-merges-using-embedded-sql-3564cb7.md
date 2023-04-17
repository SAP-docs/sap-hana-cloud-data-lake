<!-- loio3564cb7adabb42c29cba625c136de0f6 -->

# Wide Merges Using Embedded SQL

The MERGE statement can be used to merge multiple sets of rows into a table, which may improve performance. This is called a **wide merge** or an **array merge**.

To use wide merges in Embedded SQL, prepare and then execute a MERGE statement in your code as follows:

```
EXEC SQL EXECUTE ... ARRAY <nnn>
```

where ARRAY *<nnn\>* is the last part of the EXECUTE statement. The batch size *<nnn\>* can be a host variable. The number of variables in the SQLDA must be the product of the batch size and the number of placeholders in the statement to be executed.

Each variable must be of the same type in each row of the SQLDA, or a SQLDA\_INCONSISTENT error is returned.



The following complete code example illustrates a wide merge.

```
// [widemerge.sqc]
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include "sqldef.h"

EXEC SQL INCLUDE SQLCA;

EXEC SQL WHENEVER SQLERROR { PrintSQLError();
                             goto err; };

static void PrintSQLError()
{
    char buffer[200];

    printf( "SQL error %d -- %s\n",
            SQLCODE,
            sqlerror_message( &sqlca,
                              buffer,
                              sizeof( buffer ) ) );
}

char *          ConnectStr   = "";

static void Usage()
{
    fprintf( stderr, "Usage: widemerge [options] \n" );
    fprintf( stderr, "Options:\n" );
    fprintf( stderr, "   -c conn_str     : database connection string (required)\n" );
}

static int ArgumentIsASwitch( char * arg )
{
#if defined( UNIX )
    return ( arg[0] == '-' );
#else
    return ( arg[0] == '-' ) || ( arg[0] == '/' );
#endif
}

static int ProcessOptions( char * argv[] )
{
    int             argc;
    char *          arg;
    char            opt;

#define _get_arg_param()                                                \
            arg += 2;                                                   \
            if( !arg[0] ) arg = argv[++argc];                           \
            if( arg == NULL )                                           \
            {                                                           \
                fprintf( stderr, "Missing argument parameter\n" );      \
                return( -1 );                                           \
            }
    for( argc = 1; (arg = argv[argc]) != NULL; ++ argc )
    {
        if( !ArgumentIsASwitch( arg ) ) break;
        opt = arg[1];
        switch( opt )
        {
        case 'c':
            _get_arg_param();
            ConnectStr = arg;
            break;
        default:
            fprintf( stderr, "**** Unknown option: -%c\n", opt );
            Usage();
            return( -1 );
        }
    }
    if( ConnectStr[0] == '\0' )
    {
        fprintf( stderr, "A database connection string is required.\n" );
        Usage();
        return( -1 );
    }
    return( argc );
}

static int DoMerge()
{
    SQLDA                   *sqlda;
    SQLVAR                  *var;
    char                    *region_id;
    unsigned                rep_id;
    
    EXEC SQL BEGIN DECLARE SECTION;
    char                    merge_stmt[ 200 ];
    unsigned short          batch_size;
    unsigned                row_count;
    EXEC SQL END DECLARE SECTION;

    // Create the table for inserting/merging the rows
    EXEC SQL CREATE OR REPLACE TABLE LocalSalesOrders 
            (
                ID                    integer NOT NULL,
                CustomerID            integer NOT NULL,
                OrderDate             date NOT NULL,
                FinancialCode         char(2) NULL,
                Region                char(7) NULL,
                SalesRepresentative   integer NOT NULL,
                CONSTRAINT SalesOrdersKey PRIMARY KEY (ID)
            );

    strcpy( merge_stmt, 
            "MERGE INTO LocalSalesOrders "
            "USING WITH AUTO NAME"
            "("
            "    SELECT * FROM SalesOrders"
            "    WHERE Region = ? AND SalesRepresentative = ?"
            ") AS line_items "
            "ON PRIMARY KEY "
            "WHEN NOT MATCHED THEN INSERT" );

    #define NUM_PARAMS 2
            
    batch_size = 4;
    
    sqlda = alloc_sqlda_noind( batch_size * NUM_PARAMS );
    if( sqlda == NULL )
    {
        printf( "Error allocating SQLDA\n" );
        return( SQLE_NO_MEMORY );
    }

    // Prepare the static parts of the SQLDA object for the merge
    sqlda->sqld = batch_size * NUM_PARAMS;
    for( unsigned short current_row = 0; current_row < batch_size; current_row++ )
    {
        var = &sqlda->sqlvar[ current_row * NUM_PARAMS + 0 ];
        var->sqltype = DT_STRING;
        var->sqllen = 10;
        var = &sqlda->sqlvar[ current_row * NUM_PARAMS + 1 ];
        var->sqltype = DT_INT;
        var->sqllen = sizeof( int );
    }
    
    fill_sqlda( sqlda );
    
    printf( "Merge %u rowsets into table.\n", batch_size );
    
    EXEC SQL PREPARE wide_merge_stmt FROM :merge_stmt;

    // Fill in data values
    for( unsigned short current_row = 0; current_row < batch_size; current_row++ )
    {
        switch( current_row % 4 ) {
        case 0:
            region_id = "Eastern";
            rep_id = 299;
            break;
        case 1:
            region_id = "Western";
            rep_id = 299;
            break;
        case 2:
            region_id = "Eastern";
            rep_id = 856;
            break;
        case 3:
            region_id = "Western";
            rep_id = 856;
            break;
        }
        sprintf( (char *)sqlda->sqlvar[ current_row * NUM_PARAMS + 0 ].sqldata, region_id );
                 *(int *)sqlda->sqlvar[ current_row * NUM_PARAMS + 1 ].sqldata = rep_id;
    }

    // Merge batches of rowsets
    EXEC SQL EXECUTE wide_merge_stmt USING DESCRIPTOR sqlda ARRAY :batch_size;
    printf( "Merged %u rows; ", SQLCOUNT );
    // Verify count
    EXEC SQL SELECT COUNT(*) INTO :row_count FROM LocalSalesOrders;
    printf( "total %u rows in table.\n", row_count );
    
    EXEC SQL COMMIT;
    EXEC SQL DROP STATEMENT wide_merge_stmt;
    free_filled_sqlda( sqlda );
err:
    return( SQLCODE );
}

int main( int argc, char *argv[] )
{
    int     result_code;
   
    argc = ProcessOptions( argv );
    if( argc < 0 )
    {
        return( 1 );
    }

    db_init( &sqlca );

    db_string_connect( &sqlca, ConnectStr );
    if( SQLCODE != SQLE_NOERROR )
    {
        PrintSQLError();
        goto err;
    }

    result_code = DoMerge();

    EXEC SQL DISCONNECT;
    db_fini( &sqlca );
    return( (result_code == 0) ? EXIT_OKAY : EXIT_FAIL );
err:
    db_fini( &sqlca );
    return( EXIT_FAIL );
}

```



## Notes on Using Wide Merges

-   To try this example, use the sample database.

-   The size of the SQLDA is based on the size of the batch \(the maximum number of merges\) multiplied by the number of placeholder parameters in the MERGE statement. In this example, there are 2 parameters. Memory for the SQLDA is allocated using the alloc\_sqlda\_noind function. This function does not allocate space for indicator variables.

    ```
    sqlda = alloc_sqlda_noind( batch_size * NUM_PARAMS );
    ```

-   The entire SQLDA is initialized one row and parameter at a time. In general, the position in the SQLDA for each row and parameter is calculated using zero-based offsets as in the following example:

    ```
    var = &sqlda->sqlvar[ <row_index> * <num_params> + <parameter_index> ];
    var->sqltype = <column_type>;
    var->sqllen = <column_size>;
    ```

-   Once this has been done, the fill\_sqlda routine can be called to allocate buffers for the parameter values in all rows of the batch. Values are stuffed into the buffers using zero-based offsets prior to executing the prepared MERGE statement. The following is an example for storing the region string and the representative number for a given row.

    ```
    sprintf( (char *)sqlda->sqlvar[ current_row * NUM_PARAMS + 0 ].sqldata, region_id );
             *(int *)sqlda->sqlvar[ current_row * NUM_PARAMS + 1 ].sqldata = rep_id;
    ```

-   The prepared MERGE statement is executed using the EXEC SQL EXECUTE statement and the size of the batch is specified by the ARRAY clause. The following is an example.

    ```
    EXEC SQL EXECUTE wide_merge_stmt USING DESCRIPTOR sqlda ARRAY :batch_size;
    ```

-   The number of rows that were affected is returned in SQLCOUNT, which is always greater than zero unless no row matched any of the specified rows \(for example, the rows were already present\) or there is an error or warning.

    ```
    printf( "Merged %u rows; ", SQLCOUNT );
    ```


