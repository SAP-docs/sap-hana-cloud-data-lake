<!-- loio3bcffa286c5f101480f4fcb61b4e87ac -->

# Autocommit Implementation Details

Autocommit mode has slightly different behavior depending on the interface and provider that you are using and how you control the autocommit behavior.

Some application programming interfaces operate in manual commit mode by default. Others operate in automatic commit \(or autocommit\) mode by default. Consult the documentation for each API to determine which mode is default.

The way autocommit behavior is controlled depends on the application programming interface.

 API method execution
 :   To enable or disable autocommit, some application programming interfaces provide native callable methods. Examples are ADO.NET, ADO/OLE DB, JDBC, ODBC, Perl, and PHP.

    For example, in ODBC applications you enable autocommit using an API call as follows:

    ```
    SQLSetConnectAttr( hdbc, SQL_ATTR_AUTOCOMMIT, (SQLPOINTER)SQL_AUTOCOMMIT_ON, 0 );
    ```

  Statement option execution
 :   To enable or disable autocommit, some application programming interfaces require the execution of a SQL SET OPTION statement. Examples are ESQL, Python, and Ruby. The following statement temporarily enables autocommit on the database server for this connection only.

    ```
    SET TEMPORARY OPTION auto_commit='On'
    ```

    When you use the SAP Open Client interface, you set the CHAINED option to manipulate autocommit behavior. The CHAINED option is provided for TDS application compatibility. If you are using the jConnect JDBC driver, then you must call the JDBC setAutoCommit method rather than set the CHAINED option.

 > ### Note:  
> If the application programming interface provides a callable native method specifically for enabling or disabling autocommit, then that interface must be used.

