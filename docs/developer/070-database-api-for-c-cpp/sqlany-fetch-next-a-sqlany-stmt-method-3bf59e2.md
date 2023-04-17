<!-- loio3bf59e2c6c5f10149167d9077a62f556 -->

# sqlany\_fetch\_next\(a\_sqlany\_stmt \*\) Method

Returns the next set of rows from the result set.



```
public sacapi_bool sqlany_fetch_next (a_sqlany_stmt * sqlany_stmt)
```



## Parameters

sqlany\_stmt
:   A statement object that was executed by sqlany\_execute\(\) or sqlany\_execute\_direct\(\).



## Returns

1 if the fetch was successfully, 0 when the fetch is unsuccessful.



## Remarks

When the result object is first created, the current row pointer is set to before the first row, that is, row 0. This function first advances the row pointer to the next unfetched row and then fetches rows of data starting from that row. The number of rows fetched is set by the sqlany\_set\_rowset\_size\(\) function. By default, one row is returned.

**Related Information**  


[sqlany\_fetch\_absolute\(a\_sqlany\_stmt \*, sacapi\_i32\) Method](sqlany-fetch-absolute-a-sqlany-stmt-sacapi-i32-method-3bf5955.md "Moves the current row in the result set to the specified row number and then fetches rows of data starting from the current row.")

[sqlany\_execute\_direct\(a\_sqlany\_connection \*, const char \*\) Method](sqlany-execute-direct-a-sqlany-connection-const-char-method-3bf574d.md "Executes the SQL statement specified by the string argument and possibly returns a result set.")

[sqlany\_execute\(a\_sqlany\_stmt \*\) Method](sqlany-execute-a-sqlany-stmt-method-3bf58a8.md "Executes a prepared statement.")

[sqlany\_error\(a\_sqlany\_connection \*, char \*, size\_t\) Method](sqlany-error-a-sqlany-connection-char-size-t-method-3bf56ba.md "Retrieves the last error code and message stored in the connection object.")

[sqlany\_set\_rowset\_size\(a\_sqlany\_stmt \*, sacapi\_u32\) Method](sqlany-set-rowset-size-a-sqlany-stmt-sacapi-u32-method-9d0617f.md "Sets the size of the row set to be fetched by the sqlany_fetch_absolute() and sqlany_fetch_next() functions.")

