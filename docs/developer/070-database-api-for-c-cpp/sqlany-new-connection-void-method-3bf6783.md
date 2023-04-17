<!-- loio3bf6783b6c5f1014a0d1a56934d7c686 -->

# sqlany\_new\_connection\(void\) Method

Creates a connection object.



```
public a_sqlany_connection * sqlany_new_connection (void)
```



## Returns

A connection object



## Remarks

You must create an API connection object before establishing a database connection. Errors can be retrieved from the connection object. Only one request can be processed on a connection at a time. In addition, not more than one thread is allowed to access a connection object at a time. Undefined behavior or a failure occurs when multiple threads attempt to access a connection object simultaneously.

**Related Information**  


[sqlany\_connect\(a\_sqlany\_connection \*, const char \*\) Method](sqlany-connect-a-sqlany-connection-const-char-method-3bf5542.md "Creates a connection to a SQL Anywhere database server using the supplied connection object and connection string.")

[sqlany\_disconnect\(a\_sqlany\_connection \*\) Method](sqlany-disconnect-a-sqlany-connection-method-3bf563b.md "Disconnects an already established SQL Anywhere connection.")

