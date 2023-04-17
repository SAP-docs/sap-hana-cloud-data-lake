<!-- loio3bd01c5f6c5f10148aaeff37881c6f72 -->

# ODBC Connection Functions

ODBC supplies three different connection functions.

Which one you use depends on how you expect your application to be deployed and used:

SQLConnect
:   The simplest connection function.

    SQLConnect takes a data source name and optional user ID and password. Use SQLConnect if you hard-code a data source name into your application.

SQLDriverConnect
:   Connects to a data source using a connection string.

    SQLDriverConnect allows the application to use connection information that is external to the data source definition. Also, you can use SQLDriverConnect to request that the ODBC driver prompt for connection information.

    SQLDriverConnect can also be used to connect without specifying a data source. The ODBC driver name is specified instead. The following example connects to a server and database that is already running.

    ```
    SQLSMALLINT cso;
    SQLCHAR     scso[2048];
    
    SQLDriverConnect( hdbc, NULL,
       "Driver=SAP IQ;UID=DBA;PWD=passwd", SQL_NTS,
       scso, sizeof(scso)-1,
       &cso, SQL_DRIVER_NOPROMPT );
    ```

SQLBrowseConnect
:   Connects to a data source using a connection string, like SQLDriverConnect.

    SQLBrowseConnect allows your application to build its own windows to prompt for connection information and to browse for data sources used by a particular driver.

