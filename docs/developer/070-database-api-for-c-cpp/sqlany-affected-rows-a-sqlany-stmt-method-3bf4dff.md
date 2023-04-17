<!-- loio3bf4dff16c5f1014aa3bde1d7f2d6796 -->

# sqlany\_affected\_rows\(a\_sqlany\_stmt \*\) Method

Returns the number of rows affected by execution of the prepared statement.



```
public sacapi_i32 sqlany_affected_rows (a_sqlany_stmt * sqlany_stmt)
```



## Parameters

sqlany\_stmt
:   A statement that was prepared and executed successfully with no result set returned. For example, an INSERT, UPDATE or DELETE statement was executed.



## Returns

The number of rows affected or -1 on failure.

**Related Information**  


[sqlany\_execute\(a\_sqlany\_stmt \*\) Method](sqlany-execute-a-sqlany-stmt-method-3bf58a8.md "Executes a prepared statement.")

[sqlany\_execute\_direct\(a\_sqlany\_connection \*, const char \*\) Method](sqlany-execute-direct-a-sqlany-connection-const-char-method-3bf574d.md "Executes the SQL statement specified by the string argument and possibly returns a result set.")

