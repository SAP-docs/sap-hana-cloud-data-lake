<!-- loio3bf5db6b6c5f10149bf1e9f239689f84 -->

# sqlany\_free\_stmt\(a\_sqlany\_stmt \*\) Method

Frees resources associated with a prepared statement object.



```
public void sqlany_free_stmt (a_sqlany_stmt * sqlany_stmt)
```



## Parameters

sqlany\_stmt
:   A statement object returned by the successful execution of sqlany\_prepare\(\) or sqlany\_execute\_direct\(\).

**Related Information**  


[sqlany\_prepare\(a\_sqlany\_connection \*, const char \*\) Method](sqlany-prepare-a-sqlany-connection-const-char-method-3bf6a1b.md "Prepares a supplied SQL string.")

[sqlany\_execute\_direct\(a\_sqlany\_connection \*, const char \*\) Method](sqlany-execute-direct-a-sqlany-connection-const-char-method-3bf574d.md "Executes the SQL statement specified by the string argument and possibly returns a result set.")

