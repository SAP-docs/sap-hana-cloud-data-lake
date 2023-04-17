<!-- loio3bd9115a6c5f1014b10192f5a731a630 -->

# Server Options Changed by ODBC

The ODBC driver sets some temporary server options when connecting to the database server.

The following options are set as indicated.

date\_format
:   yyyy-mm-dd

date\_order
:   ymd

isolation\_level
:   based on the SQL\_ATTR\_TXN\_ISOLATION/SA\_SQL\_ATTR\_TXN\_ISOLATION attribute setting of SQLSetConnectAttr. The following options are available.

    ```
    SQL_TXN_READ_UNCOMMITTED
    SQL_TXN_READ_COMMITTED
    SQL_TXN_REPEATABLE_READ
    SQL_TXN_SERIALIZABLE
    SA_SQL_TXN_SNAPSHOT
    SA_SQL_TXN_STATEMENT_SNAPSHOT
    SA_SQL_TXN_READONLY_STATEMENT_SNAPSHOT
    ```

time\_format
:   hh:nn:ss

timestamp\_format
:   yyyy-mm-dd hh:nn:ss.ssssss

timestamp\_with\_time\_zone\_format
:   yyyy-mm-dd hh:nn:ss.ssssss +hh:nn

To guarantee consistent behavior of the ODBC driver, do not change the setting of these options.

