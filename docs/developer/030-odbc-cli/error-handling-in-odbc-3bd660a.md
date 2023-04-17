<!-- loio3bd660a36c5f10148c35ba62b373aa91 -->

# Error Handling in ODBC

Errors in ODBC are reported using the return value from each of the ODBC function calls and either the SQLError function or the SQLGetDiagRec function.

The SQLError function was used in ODBC versions up to, but not including, version 3. As of version 3 the SQLError function has been deprecated and replaced by the SQLGetDiagRec function.

Every ODBC function returns a SQLRETURN, which is one of the following status codes:


<table>
<tr>
<th valign="top">

Status Code



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

SQL\_SUCCESS



</td>
<td valign="top">

No error.



</td>
</tr>
<tr>
<td valign="top">

SQL\_SUCCESS\_WITH\_INFO



</td>
<td valign="top">

The function completed, but a call to SQLError will indicate a warning.

The most common case for this status is that a value being returned is too long for the buffer provided by the application.



</td>
</tr>
<tr>
<td valign="top">

SQL\_ERROR



</td>
<td valign="top">

The function did not complete because of an error. Call SQLError to get more information about the problem.



</td>
</tr>
<tr>
<td valign="top">

SQL\_INVALID\_HANDLE



</td>
<td valign="top">

An invalid environment, connection, or statement handle was passed as a parameter.

This often happens if a handle is used after it has been freed, or if the handle is the null pointer.



</td>
</tr>
<tr>
<td valign="top">

SQL\_NO\_DATA\_FOUND



</td>
<td valign="top">

There is no information available.

The most common use for this status is when fetching from a cursor; it indicates that there are no more rows in the cursor.



</td>
</tr>
<tr>
<td valign="top">

SQL\_NEED\_DATA



</td>
<td valign="top">

Data is needed for a parameter.

This is an advanced feature described in the ODBC SDK documentation under SQLParamData and SQLPutData.



</td>
</tr>
</table>

Every environment, connection, and statement handle can have one or more errors or warnings associated with it. Each call to SQLError or SQLGetDiagRec returns the information for one error and removes the information for that error. If you do not call SQLError or SQLGetDiagRec to remove all errors, the errors are removed on the next function call that passes the same handle as a parameter.

Each call to SQLError passes three handles for an environment, connection, and statement. The first call uses SQL\_NULL\_HSTMT to get the error associated with a connection. Similarly, a call with both SQL\_NULL\_DBC and SQL\_NULL\_HSTMT get any error associated with the environment handle.

Each call to SQLGetDiagRec can pass either an environment, connection or statement handle. The first call passes in a handle of type SQL\_HANDLE\_DBC to get the error associated with a connection. The second call passes in a handle of type SQL\_HANDLE\_STMT to get the error associated with the statement that was just executed.

SQLError and SQLGetDiagRec return SQL\_SUCCESS if there is an error to report \(*not* SQL\_ERROR\), and SQL\_NO\_DATA\_FOUND if there are no more errors to report.



Example 1
:   The following code fragment uses SQLError and return codes:

    ```
    // ODBC 2.0
    RETCODE rc;
    HENV env;
    HDBC dbc;
    HSTMT stmt;
    SDWORD err_native;
    UCHAR err_state[6];
    UCHAR err_msg[ 512 ];
    SWORD err_ind;
    
    rc = SQLAllocHandle( SQL_HANDLE_STMT, dbc, &stmt ); 
    if( rc == SQL_ERROR )
    {
       printf( "Allocation failed\n" );
       for(;;)
       {
          rc = SQLError( env, dbc, SQL_NULL_HSTMT, err_state, &err_native, 
                   err_msg, sizeof(err_msg), &err_ind );
          if( rc  < SQL_SUCCESS ) break;
          if( rc == SQL_NO_DATA_FOUND ) break;
          printf( "[%s:%d] %s\n", err_state, err_native, err_msg );
       }
       return;
    }
    
    rc = SQLExecDirect( stmt,
           "DELETE FROM SalesOrderItems WHERE ID=2015",
           SQL_NTS ); 
    if( rc == SQL_ERROR ) 
    {
       printf( "Failed to delete items\n" );
       for(;;)
       {
          rc = SQLError( env, dbc, stmt, err_state, &err_native, 
                   err_msg, sizeof(err_msg), &err_ind );
          if( rc  < SQL_SUCCESS ) break;
          if( rc == SQL_NO_DATA_FOUND ) break;
          printf( "[%s:%d] %s\n", err_state, err_native, err_msg );
       }
       return;
    }
    ```

Example 2
:   The following code fragment uses SQLGetDiagRec and return codes:

    ```
    // ODBC 3.0
    SQLRETURN rc;
    SQLHDBC dbc;
    SQLHSTMT stmt;
    SQLSMALLINT rec;
    SQLINTEGER err_native;
    SQLCHAR err_state[6];
    SQLCHAR err_msg[ 512 ];
    SQLSMALLINT err_ind; 
    
    rc = SQLAllocHandle( SQL_HANDLE_STMT, dbc, &stmt );
    if( rc == SQL_ERROR )
    {
       printf( "Failed to allocate handle\n" );
       for( rec = 1; ; rec++ )
       {
          rc = SQLGetDiagRec( SQL_HANDLE_DBC, dbc, rec, err_state, &err_native, 
                   err_msg, sizeof(err_msg), &err_ind );
          if( rc  < SQL_SUCCESS ) break;
          if( rc == SQL_NO_DATA_FOUND ) break;
          printf( "[%s:%d] %s\n", err_state, err_native, err_msg );
       }
       return;
    }
    
    rc = SQLExecDirect( stmt,
           "DELETE FROM SalesOrderItems WHERE ID=2015",
           SQL_NTS ); 
    if( rc == SQL_ERROR ) 
    {
       printf( "Failed to delete items\n" );
       for( rec = 1; ; rec++ )
       {
          rc = SQLGetDiagRec( SQL_HANDLE_STMT, stmt, rec, err_state, &err_native, 
                   err_msg, sizeof(err_msg), &err_ind );
          if( rc  < SQL_SUCCESS ) break;
          if( rc == SQL_NO_DATA_FOUND ) break;
          printf( "[%s:%d] %s\n", err_state, err_native, err_msg );
       }
       return;
    }
    ```

