<!-- loio3bf56ba06c5f10148011e6fa673965a8 -->

# sqlany\_error\(a\_sqlany\_connection \*, char \*, size\_t\) Method

Retrieves the last error code and message stored in the connection object.



```
public sacapi_i32 sqlany_error (
    a_sqlany_connection * sqlany_conn,
    char * buffer,
    size_t size
)
```



## Parameters

sqlany\_conn
:   A connection object returned from sqlany\_new\_connection\(\).

buffer
:   A buffer to be filled with the error message.

size
:   The size of the supplied buffer.



## Returns

The last error code. Positive values are warnings, negative values are errors, and 0 indicates success.

**Related Information**  


[sqlany\_connect\(a\_sqlany\_connection \*, const char \*\) Method](sqlany-connect-a-sqlany-connection-const-char-method-3bf5542.md "Creates a connection to a SQL Anywhere database server using the supplied connection object and connection string.")

