<!-- loio3bf659996c5f1014871f9ac346d9b3a3 -->

# sqlany\_make\_connection\_ex\(a\_sqlany\_interface\_context \*, void \*\) Method

Creates a connection object based on a supplied DBLIB SQLCA pointer and context.



```
public a_sqlany_connection * sqlany_make_connection_ex (
    a_sqlany_interface_context * context,
    void * arg
)
```



## Parameters

context
:   A valid context object that was created by sqlany\_init\_ex\(\)

arg
:   A void \* pointer to a DBLIB SQLCA object.



## Returns

A connection object.

**Related Information**  


[sqlany\_init\_ex\(const char \*, sacapi\_u32, sacapi\_u32 \*\) Method](sqlany-init-ex-const-char-sacapi-u32-sacapi-u32-method-3bf6493.md "Initializes the interface using a context.")

[sqlany\_execute\(a\_sqlany\_stmt \*\) Method](sqlany-execute-a-sqlany-stmt-method-3bf58a8.md "Executes a prepared statement.")

[sqlany\_execute\_direct\(a\_sqlany\_connection \*, const char \*\) Method](sqlany-execute-direct-a-sqlany-connection-const-char-method-3bf574d.md "Executes the SQL statement specified by the string argument and possibly returns a result set.")

[sqlany\_execute\_immediate\(a\_sqlany\_connection \*, const char \*\) Method](sqlany-execute-immediate-a-sqlany-connection-const-char-method-3bf5802.md "Executes the supplied SQL statement immediately without returning a result set.")

[sqlany\_prepare\(a\_sqlany\_connection \*, const char \*\) Method](sqlany-prepare-a-sqlany-connection-const-char-method-3bf6a1b.md "Prepares a supplied SQL string.")

