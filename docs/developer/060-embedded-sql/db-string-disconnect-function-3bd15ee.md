<!-- loio3bd15eeb6c5f101482a8819cbafe6024 -->

# db\_string\_disconnect Function

Disconnect the current or other connection from a database on a database server.



```
unsigned int db_string_disconnect(
    SQLCA * <sqlca>, 
    char * <parms> );
```



## Parameters

 sqlca
 :   A pointer to a SQLCA structure.

  parms
 :   A null-terminated string containing a semicolon-delimited list of connection parameters, each of the form keyword=*<value\>*. For example:

    ```
    "DSN=SAP IQ 17 Demo;ConnectionName=esql-con-20130228;PWD=sql"
    ```

 

## Returns

Non-zero if successful; 0 otherwise.



## Remarks

This function disconnects the connection identified by the ConnectionName \(CON\) connection parameter, if one is specified. All other parameters are ignored.

If no ConnectionName parameter is specified in the string, the unnamed connection is disconnected. This is equivalent to the Embedded SQL DISCONNECT statement. The return value is TRUE if a connection was successfully ended. Error information is returned in the SQLCA.

This function shuts down the database if it was started with the AutoStop=yes connection parameter and there are no other connections to the database. It also stops the server if it was started with the AutoStop=yes parameter and there are no other databases running.

