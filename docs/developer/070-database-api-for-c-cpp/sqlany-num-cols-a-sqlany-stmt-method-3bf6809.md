<!-- loio3bf680946c5f101489a8e51f835e7997 -->

# sqlany\_num\_cols\(a\_sqlany\_stmt \*\) Method

Returns number of columns in the result set.



```
public sacapi_i32 sqlany_num_cols (a_sqlany_stmt * sqlany_stmt)
```



## Parameters

sqlany\_stmt
:   A statement object created by sqlany\_prepare\(\) or sqlany\_execute\_direct\(\).



## Returns

The number of columns in the result set or -1 on a failure.

**Related Information**  


[sqlany\_execute\(a\_sqlany\_stmt \*\) Method](sqlany-execute-a-sqlany-stmt-method-3bf58a8.md "Executes a prepared statement.")

[sqlany\_execute\_direct\(a\_sqlany\_connection \*, const char \*\) Method](sqlany-execute-direct-a-sqlany-connection-const-char-method-3bf574d.md "Executes the SQL statement specified by the string argument and possibly returns a result set.")

[sqlany\_prepare\(a\_sqlany\_connection \*, const char \*\) Method](sqlany-prepare-a-sqlany-connection-const-char-method-3bf6a1b.md "Prepares a supplied SQL string.")

