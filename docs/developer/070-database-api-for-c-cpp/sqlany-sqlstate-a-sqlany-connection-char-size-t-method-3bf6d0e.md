<!-- loio3bf6d0ea6c5f1014ae30f4098663137c -->

# sqlany\_sqlstate\(a\_sqlany\_connection \*, char \*, size\_t\) Method

Retrieves the current SQLSTATE.



```
public size_t sqlany_sqlstate (
    a_sqlany_connection * sqlany_conn,
    char * buffer,
    size_t size
)
```



## Parameters

sqlany\_conn
:   A connection object returned from sqlany\_new\_connection\(\).

buffer
:   A buffer to be filled with the current 5-character SQLSTATE.

size
:   The buffer size.



## Returns

The number of bytes copied into the buffer.

**Related Information**  


[sqlany\_error\(a\_sqlany\_connection \*, char \*, size\_t\) Method](sqlany-error-a-sqlany-connection-char-size-t-method-3bf56ba.md "Retrieves the last error code and message stored in the connection object.")

