<!-- loio3bf697bc6c5f1014b05fc7590614f2bd -->

# sqlany\_num\_rows\(a\_sqlany\_stmt \*\) Method

Returns the number of rows in the result set.



```
public sacapi_i32 sqlany_num_rows (a_sqlany_stmt * sqlany_stmt)
```



## Parameters

sqlany\_stmt
:   A statement object that was executed by sqlany\_execute\(\) or sqlany\_execute\_direct\(\).



## Returns

The number rows in the result set. If the number of rows is an estimate, the number returned is negative and the estimate is the absolute value of the returned integer. The value returned is positive if the number of rows is exact.



## Remarks

By default this function only returns an estimate. To return an exact count, set the row\_counts option on the connection.

**Related Information**  


[sqlany\_execute\_direct\(a\_sqlany\_connection \*, const char \*\) Method](sqlany-execute-direct-a-sqlany-connection-const-char-method-3bf574d.md "Executes the SQL statement specified by the string argument and possibly returns a result set.")

[sqlany\_execute\(a\_sqlany\_stmt \*\) Method](sqlany-execute-a-sqlany-stmt-method-3bf58a8.md "Executes a prepared statement.")

