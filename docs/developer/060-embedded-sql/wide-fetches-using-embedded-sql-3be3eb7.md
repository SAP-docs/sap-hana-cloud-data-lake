<!-- loio3be3eb786c5f1014944ff4ed54048da6 -->

# Wide Fetches Using Embedded SQL

The FETCH statement can be modified to fetch more than one row at a time, which may improve performance. This is called a **wide fetch** or an **array fetch**.

Wide puts and inserts are also supported.

To use wide fetches in Embedded SQL, include the FETCH statement in your code as follows:

```
EXEC SQL FETCH ... ARRAY <nnn>
```

where ARRAY *<nnn\>* is the last item of the FETCH statement. The fetch count *<nnn\>* can be a host variable. The number of variables in the SQLDA must be the product of *<nnn\>* and the number of columns per row. The first row is placed in SQLDA variables 0 to \(columns per row\) - 1, and so on.

Each column must be of the same type in each row of the SQLDA, or a SQLDA\_INCONSISTENT error is returned.

The server returns in SQLCOUNT the number of records that were fetched, which is always greater than zero unless there is an error or warning. On a wide fetch, a SQLCOUNT of 1 with no error condition indicates that one valid row has been fetched.



The following example code illustrates the use of wide fetches. The complete example is found in <code><i>%IQDIRSAMP17%</i>\SQLAnywhere\esqlwidefetch\widefetch.sqc</code>.

```
static SQLDA * PrepareSQLDA(
        a_sql_statement_number  stat0,
        unsigned                width,
        unsigned                *cols_per_row )
{
    int                     num_cols;
    unsigned                row, col, offset;
    SQLDA *                 sqlda;
    EXEC SQL BEGIN DECLARE SECTION;
    a_sql_statement_number  stat;
    EXEC SQL END DECLARE SECTION;

    stat = stat0;
    sqlda = alloc_sqlda( 100 );
    if( sqlda == NULL ) return( NULL );
    EXEC SQL DESCRIBE :stat INTO sqlda;
    *cols_per_row = num_cols = sqlda->sqld;
    if( num_cols * width > sqlda->sqln ) {
        free_sqlda( sqlda );
        sqlda = alloc_sqlda( num_cols * width );
        if( sqlda == NULL ) return( NULL );
        EXEC SQL DESCRIBE :stat INTO sqlda;
    }
    // copy first row in SQLDA setup by describe
    // to following (wide) rows
    sqlda->sqld = num_cols * width;
    offset = num_cols;
    for( row = 1; row < width; row++ ) {
        for( col = 0; col < num_cols; col++, offset++ ) {
            sqlda->sqlvar[offset].sqltype = sqlda->sqlvar[col].sqltype;
            sqlda->sqlvar[offset].sqllen = sqlda->sqlvar[col].sqllen;
            // optional: copy described column name
            memcpy( &sqlda->sqlvar[offset].sqlname,
                    &sqlda->sqlvar[col].sqlname,
                    sizeof( sqlda->sqlvar[0].sqlname ) );
        }
    }
    fill_s_sqlda( sqlda, 40 );
    return( sqlda );

err:
    return( NULL );
}

static void PrintFetchedRows( SQLDA * sqlda,
                              unsigned cols_per_row )
{
    long                    rows_fetched;
    int                     row, col, offset;

    if( SQLCOUNT == 0 ) {
        rows_fetched = 1;
    } else {
        rows_fetched = SQLCOUNT;
    }
    printf( "Fetched %d Rows:\n", rows_fetched );
    for( row = 0; row < rows_fetched; row++ ) {
        for( col = 0; col < cols_per_row; col++ ) {
            offset = row * cols_per_row + col;
            printf( " \"%s\"", (char *)sqlda->sqlvar[offset].sqldata );
        }
        printf( "\n" );
    }
}

static int DoQuery( char * query_str0,
                    unsigned fetch_width0 )
{
    SQLDA *                 sqlda;
    unsigned                cols_per_row;
    
    EXEC SQL BEGIN DECLARE SECTION;
    a_sql_statement_number  stat;
    char *                  query_str;
    unsigned                fetch_width;
    EXEC SQL END DECLARE SECTION;

    query_str = query_str0;
    fetch_width = fetch_width0;

    EXEC SQL PREPARE :stat FROM :query_str;
    EXEC SQL DECLARE QCURSOR CURSOR FOR :stat FOR READ ONLY;
    EXEC SQL OPEN QCURSOR;
    sqlda = PrepareSQLDA( stat, fetch_width, &cols_per_row );
    if( sqlda == NULL ) {
        printf( "Error allocating SQLDA\n" );
        return( SQLE_NO_MEMORY );
    }
    for( ;; ) {
        EXEC SQL FETCH QCURSOR INTO DESCRIPTOR sqlda ARRAY :fetch_width;
        if( SQLCODE != SQLE_NOERROR ) break;
        PrintFetchedRows( sqlda, cols_per_row );
    }
    EXEC SQL CLOSE QCURSOR;
    EXEC SQL DROP STATEMENT :stat;
    free_filled_sqlda( sqlda );
err:
    return( SQLCODE );
}

int main( int argc, char *argv[] )
{
    int     result_code;
   
    argc = ProcessOptions( argv );
    if( argc < 0 ) {
        return( 1 );
    }

    db_init( &sqlca );

    db_string_connect( &sqlca, ConnectStr );
    if( SQLCODE != SQLE_NOERROR ) {
        PrintSQLError();
        goto err;
    }

    result_code = DoQuery( QueryStr, FetchWidth );

    EXEC SQL DISCONNECT;
    db_fini( &sqlca );
    return( (result_code == 0) ? EXIT_OKAY : EXIT_FAIL );
err:
    db_fini( &sqlca );
    return( EXIT_FAIL );
}
```



## Notes on Using Wide Fetches

-   In the function PrepareSQLDA, the SQLDA memory is allocated using the alloc\_sqlda function. This allows space for indicator variables, rather than using the alloc\_sqlda\_noind function.

-   If the number of rows fetched is fewer than the number requested, but is not zero \(at the end of the cursor for example\), the SQLDA items corresponding to the rows that were not fetched are returned as NULL by setting the indicator value. If no indicator variables are present, an error is generated \(SQLE\_NO\_INDICATOR: no indicator variable for NULL result\).

-   If a row being fetched has been updated, generating a SQLE\_ROW\_UPDATED\_WARNING warning, the fetch stops on the row that caused the warning. The values for all rows processed to that point \(including the row that caused the warning\) are returned. SQLCOUNT contains the number of rows that were fetched, including the row that caused the warning. All remaining SQLDA items are marked as NULL.

-   If a row being fetched has been deleted or is locked, generating a SQLE\_NO\_CURRENT\_ROW or SQLE\_LOCKED error, SQLCOUNT contains the number of rows that were read before the error. This does not include the row that caused the error. The SQLDA does not contain values for any of the rows since SQLDA values are not returned on errors. The SQLCOUNT value can be used to reposition the cursor, if necessary, to read the rows.


