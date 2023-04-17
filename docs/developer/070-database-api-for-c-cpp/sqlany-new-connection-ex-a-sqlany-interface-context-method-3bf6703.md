<!-- loio3bf670306c5f1014bf1db3c92e8e9a7e -->

# sqlany\_new\_connection\_ex\(a\_sqlany\_interface\_context \*\) Method

Creates a connection object using a context.



```
public a_sqlany_connection * sqlany_new_connection_ex (a_sqlany_interface_context * context)
```



## Parameters

context
:   A context object that was returned from sqlany\_init\_ex\(\)



## Returns

A connection object

**Related Information**  


[sqlany\_connect\(a\_sqlany\_connection \*, const char \*\) Method](sqlany-connect-a-sqlany-connection-const-char-method-3bf5542.md "Creates a connection to a SQL Anywhere database server using the supplied connection object and connection string.")

[sqlany\_disconnect\(a\_sqlany\_connection \*\) Method](sqlany-disconnect-a-sqlany-connection-method-3bf563b.md "Disconnects an already established SQL Anywhere connection.")

[sqlany\_init\_ex\(const char \*, sacapi\_u32, sacapi\_u32 \*\) Method](sqlany-init-ex-const-char-sacapi-u32-sacapi-u32-method-3bf6493.md "Initializes the interface using a context.")

