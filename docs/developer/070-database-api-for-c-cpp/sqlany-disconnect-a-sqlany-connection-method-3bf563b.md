<!-- loio3bf563b76c5f1014b025f40dda6b94f2 -->

# sqlany\_disconnect\(a\_sqlany\_connection \*\) Method

Disconnects an already established SQL Anywhere connection.



```
public sacapi_bool sqlany_disconnect (a_sqlany_connection * sqlany_conn)
```



## Parameters

sqlany\_conn
:   A connection object with a connection established using sqlany\_connect\(\).



## Returns

1 when successful or 0 when unsuccessful.



## Remarks

All uncommitted transactions are rolled back.

**Related Information**  


[sqlany\_connect\(a\_sqlany\_connection \*, const char \*\) Method](sqlany-connect-a-sqlany-connection-const-char-method-3bf5542.md "Creates a connection to a SQL Anywhere database server using the supplied connection object and connection string.")

[sqlany\_new\_connection\(void\) Method](sqlany-new-connection-void-method-3bf6783.md "Creates a connection object.")

