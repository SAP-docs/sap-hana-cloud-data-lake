<!-- loio3bd156a36c5f10148a3af7ed0ad6ca66 -->

# db\_string\_connect Function

Connect to a database on a database server.



```
unsigned int db_string_connect( SQLCA * <sqlca>, char * <parms> );
```



## Parameters

 sqlca
 :   A pointer to a SQLCA structure.

  parms
 :   A null-terminated string containing a semicolon-delimited list of parameter settings, each of the form KEYWORD=*<value\>*. For example:

    ```
    "UID=HDLADMIN;PWD=<password>;DBF=c:\\db\\mydatabase.db"
    ```

 

## Returns

Non-zero if successful; 0 otherwise.



## Remarks

Provides extra functionality beyond the Embedded SQL CONNECT statement.

The algorithm used by this function is described in the troubleshooting connections topic.

The return value is TRUE \(non-zero\) if a connection was successfully established and FALSE \(zero\) otherwise. Error information for starting the server, starting the database, or connecting is returned in the SQLCA.

