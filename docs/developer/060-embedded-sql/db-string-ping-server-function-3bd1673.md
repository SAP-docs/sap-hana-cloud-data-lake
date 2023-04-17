<!-- loio3bd167316c5f1014951ef6c7d329dd7d -->

# db\_string\_ping\_server Function

Determine if a server can be located, and optionally, if it a successful connection to a database can be made.



```
unsigned int db_string_ping_server(
SQLCA * <sqlca>,
char * <connect_string>,
unsigned int <connect_to_db> );
```



## Parameters

sqlca
:   A pointer to a SQLCA structure.

connect\_string
:   The *<connect\_string\>* is a normal connection string that may or may not contain server and database information.

connect\_to\_db
:   If *<connect\_to\_db\>* is non-zero \(TRUE\), then the function attempts to connect to a database on a server. It returns TRUE only if the connection string is sufficient to connect to the named database on the named server.

    If *<connect\_to\_db\>* is zero, then the function only attempts to locate a server. It returns TRUE only if the connection string is sufficient to locate a server. It makes no attempt to connect to the database.



## Returns

TRUE \(non-zero\) if the server or database was successfully located; FALSE \(zero\) otherwise. Error information for locating the server or database is returned in the SQLCA.



## Remarks

This function can be used to determine if a server can be located, and optionally, if it a successful connection to a database can be made.

