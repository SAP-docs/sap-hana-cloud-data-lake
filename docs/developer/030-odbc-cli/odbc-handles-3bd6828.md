<!-- loio3bd6828d6c5f1014ba1cdf08b9a4fd7d -->

# ODBC Handles

ODBC applications use a small set of **handles** to track the ODBC context, database connections, and SQL statements. A handle is a pointer type and is a 64-bit value in 64-bit applications and a 32-bit value in 32-bit applications.

The following handles are used in ODBC applications:

Environment
:   The environment handle provides a global context in which to access data. Every ODBC application must allocate exactly one environment handle upon starting, and must free it at the end.

    The following code illustrates how to allocate an environment handle:

    ```
    SQLRETURN rc;
    SQLHENV env;
    rc = SQLAllocHandle( SQL_HANDLE_ENV, SQL_NULL_HANDLE, &env );
    ```

Connection
:   A connection is the link between an application and a data source. An application can have several connections associated with its environment. Allocating a connection handle does not establish a connection; a connection handle must be allocated first and then used to establish a connection.

    The following code illustrates how to allocate a connection handle:

    ```
    SQLRETURN rc;
    SQLHDBC  dbc;
    rc = SQLAllocHandle( SQL_HANDLE_DBC, env, &dbc );
    ```

Statement
:   A statement handle is used to execute SQL statements and set up or process any information associated with it, such as parameters and result sets. Each connection can have several statement handles associated with it. Statement handles are used both for query execution \(cursor operations such as fetching\) and for non-query execution \(for example, INSERT, UPDATE, and DELETE statements\).

    The following code illustrates how to allocate a statement handle:

    ```
    SQLRETURN rc;
    SQLHSTMT stmt;
    rc = SQLAllocHandle( SQL_HANDLE_STMT, dbc, &stmt );
    ```

