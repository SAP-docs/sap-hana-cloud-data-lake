<!-- loio3bd9767f6c5f1014bcf2de4ade228462 -->

# Establishing an ODBC Connection

Establish an ODBC connection in your application to perform any database operations.



## Context

You can find a complete sample in <code><i>%IQDIRSAMP17%</i>\SQLAnywhere\ODBCConnect\odbcconnect.cpp</code>.



## Procedure

1.  Allocate an ODBC environment. For example:

    ```
    SQLRETURN rc;
    SQLHENV   env;
    rc = SQLAllocHandle( SQL_HANDLE_ENV, SQL_NULL_HANDLE, &env );
    ```

2.  Declare the ODBC version. For example:

    ```
    rc = SQLSetEnvAttr( env, SQL_ATTR_ODBC_VERSION, (void*)SQL_OV_ODBC3, 0 );
    ```

    By declaring that the application follows ODBC version 3, SQLSTATE values and some other version-dependent features are set to the proper behavior.

3.  Allocate an ODBC connection handle. For example:

    ```
    rc = SQLAllocHandle( SQL_HANDLE_DBC, env, &dbc );
    ```

4.  Set any connection attributes that must be set before connecting.

    Some connection attributes must be set before establishing a connection or after establishing a connection, while others can be set either before or after. The SQL\_AUTOCOMMIT attribute is one that can be set before or after:

    ```
    rc = SQLSetConnectAttr( dbc, SQL_AUTOCOMMIT, (SQLPOINTER)SQL_AUTOCOMMIT_OFF, 0 );
    ```

    By default, ODBC operates in autocommit mode. This mode is turned off by setting SQL\_AUTOCOMMIT to false.

5.  If necessary, assemble the data source or connection string.

    Depending on your application, you may have a hard-coded data source or connection string, or you may store it externally for greater flexibility.

6.  Establish an ODBC connection. For example:

    ```
    if (rc == SQL_SUCCESS || rc == SQL_SUCCESS_WITH_INFO) 
    {
       printf( "dbc allocated\n" );
       rc = SQLConnect( dbc,
          (SQLCHAR *) "SAP IQ 17 Demo", SQL_NTS,
          (SQLCHAR *) my_userid, SQL_NTS,
          (SQLCHAR *) my_password, SQL_NTS );
       if (rc == SQL_SUCCESS || rc == SQL_SUCCESS_WITH_INFO)
       {
           // Successfully connected.
    ```

    Every string passed to ODBC has a corresponding length. If the length is unknown, you can pass SQL\_NTS indicating that it is a **Null Terminated String** whose end is marked by the null character \(\\0\) for ASCII strings or the null wide character \(\\0\\0\) for wide-character strings.




## Results

The application, when built and run, establishes an ODBC connection.

