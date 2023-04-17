<!-- loio3bf554266c5f1014abcbe2f158473020 -->

# sqlany\_connect\(a\_sqlany\_connection \*, const char \*\) Method

Creates a connection to a SQL Anywhere database server using the supplied connection object and connection string.



```
public sacapi_bool sqlany_connect (
    a_sqlany_connection * sqlany_conn,
    const char * str
)
```



## Parameters

sqlany\_conn
:   A connection object created by sqlany\_new\_connection\(\).

str
:   A SQL Anywhere connection string.



## Returns

1 if the connection is established successfully or 0 when the connection fails. Use sqlany\_error\(\) to retrieve the error code and message.



## Remarks

The supplied connection object must first be allocated using sqlany\_new\_connection\(\).

The following example demonstrates how to retrieve the error code of a failed connection attempt:

```
a_sqlany_connection * sqlany_conn;
sqlany_conn = sqlany_new_connection();
if( !sqlany_connect( sqlany_conn, "uid=hdladmin;pwd=passwd" ) ) {
   char reason[SACAPI_ERROR_SIZE];
   sacapi_i32 code;
   code = sqlany_error( sqlany_conn, reason, sizeof(reason) );
   printf( "Connection failed. Code: %d Reason: %s\n", code, reason );
} else {
   printf( "Connected successfully!\n" );
   sqlany_disconnect( sqlany_conn );
}
sqlany_free_connection( sqlany_conn );
```

**Related Information**  


[sqlany\_new\_connection\(void\) Method](sqlany-new-connection-void-method-3bf6783.md "Creates a connection object.")

[sqlany\_error\(a\_sqlany\_connection \*, char \*, size\_t\) Method](sqlany-error-a-sqlany-connection-char-size-t-method-3bf56ba.md "Retrieves the last error code and message stored in the connection object.")

