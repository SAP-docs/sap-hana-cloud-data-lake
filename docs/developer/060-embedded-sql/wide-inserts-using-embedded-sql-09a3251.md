<!-- loio09a325147c7048ca8968ac0c76d3712f -->

# Wide Inserts Using Embedded SQL

The INSERT statement can be used to insert more than one row at a time, which may improve performance. This is called a **wide insert** or an **array insert**.

To use wide inserts in Embedded SQL, prepare and then execute an INSERT statement in your code as follows:

```
EXEC SQL EXECUTE ... ARRAY <nnn>
```

where ARRAY *<nnn\>* is the last part of the EXECUTE statement. The batch size *<nnn\>* can be a host variable. The number of variables in the SQLDA must be the product of the batch size and the number of placeholders in the statement to be executed.

Each variable must be of the same type in each row of the SQLDA, or a SQLDA\_INCONSISTENT error is returned.



The following complete code example illustrates the use of wide inserts.

```
// [wideinsert.sqc]
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

unsigned        RowsToInsert = 20;
unsigned short  BatchSize    = 5;
char *          ConnectStr   = "";

static void Usage()
{
    fprintf( stderr, "Usage: wideinsert [options] \n" );
    fprintf( stderr, "Options:\n" );
    fprintf( stderr, "   -n nnn          : number of rows to insert (default: 20)\n" );
    fprintf( stderr, "   -b nnn          : insert nnn rows at a time (default: 5)\n" );
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
        case 'n':
            _get_arg_param();
            RowsToInsert = atol( arg );
            break;
        case 'b':
            _get_arg_param();
            BatchSize = (unsigned short) atol( arg );
            break;
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

static int DoInsert( unsigned rows_to_insert, unsigned short batch_size )
{
    SQLDA                   *sqlda;
    SQLVAR                  *var;
    int                     row_number = 1;
    
    EXEC SQL BEGIN DECLARE SECTION;
    char                    insert_stmt[ 100 ];
    unsigned short          array_size;
    unsigned                row_count;
    EXEC SQL END DECLARE SECTION;

    // Create the table for inserting the rows
    EXEC SQL DROP TABLE IF EXISTS WideInsertSample;
    EXEC SQL CREATE TABLE WideInsertSample( Col1 int, Col2 char(20), Col3 int );

    #define NUM_PARAMS 3
    sprintf( insert_stmt, "INSERT INTO WideInsertSample( Col1, Col2, Col3 ) VALUES( ?, ?, ? )" );
    
    sqlda = alloc_sqlda_noind( batch_size * NUM_PARAMS );
    if( sqlda == NULL )
    {
        printf( "Error allocating SQLDA\n" );
        return( SQLE_NO_MEMORY );
    }
    
    // Prepare the static parts of the SQLDA object for the insert   
    sqlda->sqld = batch_size * NUM_PARAMS;
    for( unsigned short current_row = 0; current_row < batch_size; current_row++ )
    {
        var = &sqlda->sqlvar[ current_row * NUM_PARAMS + 0 ];
        var->sqltype = DT_INT;
        var->sqllen = sizeof( int );

        var = &sqlda->sqlvar[ current_row * NUM_PARAMS + 1 ];
        var->sqltype = DT_STRING;
        var->sqllen = 30;

        var = &sqlda->sqlvar[ current_row * NUM_PARAMS + 2 ];
        var->sqltype = DT_INT;
        var->sqllen = sizeof( int );
   }
    
    fill_sqlda( sqlda );
    
    printf( "Insert %u rows into table \"WideInsertSample\" with batch size %u.\n", 
        rows_to_insert, 
        batch_size );
    
    EXEC SQL PREPARE wide_insert_stmt FROM :insert_stmt;
    while( rows_to_insert > 0 )
    {
        if( rows_to_insert > batch_size )
        {
            array_size = batch_size;
        }
        else
        {
            array_size = (unsigned short) rows_to_insert;
        }

        // Fill in data values
        for( unsigned short current_row = 0; current_row < array_size; current_row++ )
        {
            *(int *)sqlda->sqlvar[ current_row * NUM_PARAMS + 0 ].sqldata = row_number;
            sprintf( (char *)sqlda->sqlvar[ current_row * NUM_PARAMS + 1 ].sqldata,
                     "This is row #%u", row_number );
            *(int *)sqlda->sqlvar[ current_row * NUM_PARAMS + 2 ].sqldata = row_number * 2;
            row_number++;
        }

        // Insert a batch of rows
        EXEC SQL EXECUTE wide_insert_stmt USING DESCRIPTOR sqlda ARRAY :array_size;
        printf( "Inserted %u rows; ", SQLCOUNT );
        
        EXEC SQL SELECT COUNT(*) INTO :row_count FROM WideInsertSample;
        printf( "total %u rows in table.\n", row_count );
        
        rows_to_insert -= array_size;
    }
    printf( "Done.\n" );
    
    EXEC SQL COMMIT;
    EXEC SQL DROP STATEMENT wide_insert_stmt;
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

    result_code = DoInsert( RowsToInsert, BatchSize );

    EXEC SQL DISCONNECT;
    db_fini( &sqlca );
    return( (result_code == 0) ? EXIT_OKAY : EXIT_FAIL );
err:
    db_fini( &sqlca );
    return( EXIT_FAIL );
}
```



## Notes on Using Wide Inserts

-   The size of the SQLDA is based on the size of the batch \(the maximum number of rows that you want to insert at a time\) multiplied by the number of parameters or columns that you want to insert \(NUM\_PARAMS in the following examples\). Memory for the SQLDA is allocated using the alloc\_sqlda\_noind function. This function does not allocate space for indicator variables.

    ```
    sqlda = alloc_sqlda_noind( batch_size * NUM_PARAMS );
    ```

-   The entire SQLDA is initialized one row and column at a time. In general, the position in the SQLDA for each row and column is calculated using zero-based offsets as in the following example:

    ```
    var = &sqlda->sqlvar[ <row_index> * <num_params> + <parameter_index> ]
    var->sqltype = <column_type>;
    var->sqllen = <column_size>;
    ```

-   Once this has been done, the fill\_sqlda routine can be called to allocate buffers for the column values in all rows of the batch. Values are stuffed into the buffers using zero-based offsets prior to executing the prepared INSERT statement. The following is an example for storing an integer value.

    ```
    *(int *)sqlda->sqlvar[ current_row * NUM_PARAMS + current_column ].sqldata = row_number * 2;
    ```

-   The prepared INSERT statement is executed using the EXEC SQL EXECUTE statement and the number of rows to insert is specified by the ARRAY clause. The following is an example.

    ```
    EXEC SQL EXECUTE wide_insert_stmt USING DESCRIPTOR sqlda ARRAY :array_size;
    ```

-   The number of rows that were inserted is returned in SQLCOUNT, which is always greater than zero unless there is an error or warning.

    ```
    printf( "Inserted %u rows; ", SQLCOUNT );
    ```


