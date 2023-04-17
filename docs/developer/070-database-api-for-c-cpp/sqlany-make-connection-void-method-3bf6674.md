<!-- loio3bf6674d6c5f1014a40bfc8feec104fd -->

# sqlany\_make\_connection\(void \*\) Method

Creates a connection object based on a supplied DBLIB SQLCA pointer.



```
public a_sqlany_connection * sqlany_make_connection (void * arg)
```



## Parameters

arg
:   A void \* pointer to a DBLIB SQLCA object.



## Returns

A connection object.

**Related Information**  


[sqlany\_new\_connection\(void\) Method](sqlany-new-connection-void-method-3bf6783.md "Creates a connection object.")

[sqlany\_execute\(a\_sqlany\_stmt \*\) Method](sqlany-execute-a-sqlany-stmt-method-3bf58a8.md "Executes a prepared statement.")

[sqlany\_execute\_direct\(a\_sqlany\_connection \*, const char \*\) Method](sqlany-execute-direct-a-sqlany-connection-const-char-method-3bf574d.md "Executes the SQL statement specified by the string argument and possibly returns a result set.")

[sqlany\_execute\_immediate\(a\_sqlany\_connection \*, const char \*\) Method](sqlany-execute-immediate-a-sqlany-connection-const-char-method-3bf5802.md "Executes the supplied SQL statement immediately without returning a result set.")

[sqlany\_prepare\(a\_sqlany\_connection \*, const char \*\) Method](sqlany-prepare-a-sqlany-connection-const-char-method-3bf6a1b.md "Prepares a supplied SQL string.")

