<!-- loio059e6b77b92340d5997be0ed768ed289 -->

# Wide Deletes Using Embedded SQL

The DELETE statement can be used to delete an arbitrary set of rows, which may improve performance. This is called a **wide delete** or an **array delete**.

To use wide deletes in Embedded SQL, prepare and then execute a DELETE statement in your code as follows:

```
EXEC SQL EXECUTE ... ARRAY <nnn>
```

where ARRAY *<nnn\>* is the last part of the EXECUTE statement. The batch size *<nnn\>* can be a host variable. The number of variables in the SQLDA must be the product of the batch size and the number of placeholders in the statement to be executed.

Each variable must be of the same type in each row of the SQLDA, or a SQLDA\_INCONSISTENT error is returned.



The following complete code example illustrates the use of wide deletes.

```
// [widedelete.sqc]
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

unsigned        RowsToDelete[100];
unsigned short  BatchSize    = 0;
char *          ConnectStr   = "";

static void Usage()
{
    fprintf( stderr, "Usage: widedelete [options] \n" );
    fprintf( stderr, "Options:\n" );
    fprintf( stderr, "   -n nnn          : row number to delete (specify up to 100 -n arguments)\n" );
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
            RowsToDelete[BatchSize++] = atol( arg );
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

static int DoDelete( unsigned *rows_to_delete, unsigned short batch_size )
{
    SQLDA                   *sqlda;
    SQLVAR                  *var;
    
    EXEC SQL BEGIN DECLARE SECTION;
    char                    delete_stmt[ 100 ];
    unsigned short          array_size;
    unsigned                row_count;
    EXEC SQL END DECLARE SECTION;

    sprintf( delete_stmt, "DELETE FROM WideInsertSample WHERE Col1 = ?" );
    
    sqlda = alloc_sqlda_noind( batch_size );
    if( sqlda == NULL )
    {
        printf( "Error allocating SQLDA\n" );
        return( SQLE_NO_MEMORY );
    }
    
    // Prepare the static parts of the SQLDA object for the delete
    sqlda->sqld = batch_size;
    for( unsigned short current_row = 0; current_row < batch_size; current_row++ )
    {
        var = &sqlda->sqlvar[ current_row ];
        var->sqltype = DT_INT;
        var->sqllen = sizeof( int );
    }
    
    fill_sqlda( sqlda );
    
    printf( "Delete %u rows from table \"WideInsertSample\".\n", batch_size );
    
    EXEC SQL PREPARE wide_delete_stmt FROM :delete_stmt;
    array_size = batch_size;

    // Fill in data values
    for( unsigned short current_row = 0; current_row < array_size; current_row++ )
    {
        *(int *)sqlda->sqlvar[ current_row ].sqldata = rows_to_delete[ current_row ];
    }

    // Delete a batch of rows
    EXEC SQL EXECUTE wide_delete_stmt USING DESCRIPTOR sqlda ARRAY :array_size;
    printf( "Deleted %u rows; ", SQLCOUNT );
    
    EXEC SQL SELECT COUNT(*) INTO :row_count FROM WideInsertSample;
    printf( "total %u rows in table.\n", row_count );
    
    EXEC SQL COMMIT;
    EXEC SQL DROP STATEMENT wide_delete_stmt;
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

    result_code = DoDelete( RowsToDelete, BatchSize );

    EXEC SQL DISCONNECT;
    db_fini( &sqlca );
    return( (result_code == 0) ? EXIT_OKAY : EXIT_FAIL );
err:
    db_fini( &sqlca );
    return( EXIT_FAIL );
}
```



## Notes on Using Wide Deletes

-   To try this example, use the example in the wide inserts topic to populate the WideInsertSample table.

-   The size of the SQLDA is based on the size of the batch \(the maximum number of rows that you want to delete at a time\) multiplied by the number of parameters in the DELETE statement. In this example, there is only 1 parameter but you could have more. Memory for the SQLDA is allocated using the alloc\_sqlda\_noind function. This function does not allocate space for indicator variables.

    ```
    sqlda = alloc_sqlda_noind( batch_size );
    ```

-   The entire SQLDA is initialized one row and parameter at a time. In general, the position in the SQLDA for each row and parameter is calculated using zero-based offsets as in the following example \(for this DELETE example, *<num\_params\>* is 1\):

    ```
    var = &sqlda->sqlvar[ <row_index> * <num_params> + <parameter_index> ]
    var->sqltype = <column_type>;
    var->sqllen = <column_size>;
    ```

-   Once this has been done, the fill\_sqlda routine can be called to allocate buffers for the parameter values in all rows of the batch. Values are stuffed into the buffers using zero-based offsets prior to executing the prepared DELETE statement. The following is an example for storing the integer row number.

    ```
    *(int *)sqlda->sqlvar[ current_row ].sqldata = rows_to_delete[ current_row ];
    ```

-   The prepared DELETE statement is executed using the EXEC SQL EXECUTE statement and the number of rows to delete is specified by the ARRAY clause. The following is an example.

    ```
    EXEC SQL EXECUTE wide_delete_stmt USING DESCRIPTOR sqlda ARRAY :array_size;
    ```

-   The number of rows that were deleted is returned in SQLCOUNT, which is always greater than zero unless no row matched any of the specified rows \(for example, the rows were already deleted\) or there is an error or warning.

    ```
    printf( "Deleted %u rows; ", SQLCOUNT );
    ```


