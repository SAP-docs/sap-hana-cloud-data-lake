<!-- loio3bf62e466c5f10149622fc299a93587a -->

# sqlany\_get\_data\_info\(a\_sqlany\_stmt \*, sacapi\_u32, a\_sqlany\_data\_info \*\) Method

Retrieves information about the fetched data at the current row.



```
public sacapi_bool sqlany_get_data_info (
    a_sqlany_stmt * sqlany_stmt,
    sacapi_u32 col_index,
    a_sqlany_data_info * buffer
)
```



## Parameters

sqlany\_stmt
:   A statement object executed by sqlany\_execute\(\) or sqlany\_execute\_direct\(\).

col\_index
:   The column number between 0 and sqlany\_num\_cols\(\) - 1.

buffer
:   A data info buffer to be filled with the metadata about the data at the current row in the row set.



## Returns

1 on success, and 0 on failure. Failure is returned when any of the supplied parameters are invalid.



## Remarks

When a sqlany\_fetch\_absolute\(\) or sqlany\_fetch\_next\(\) function is executed, a row set is created and the current row is set to be the first row in the row set. The current row is set using the sqlany\_set\_rowset\_pos\(\) function.

**Related Information**  


[sqlany\_execute\(a\_sqlany\_stmt \*\) Method](sqlany-execute-a-sqlany-stmt-method-3bf58a8.md "Executes a prepared statement.")

[sqlany\_execute\_direct\(a\_sqlany\_connection \*, const char \*\) Method](sqlany-execute-direct-a-sqlany-connection-const-char-method-3bf574d.md "Executes the SQL statement specified by the string argument and possibly returns a result set.")

[sqlany\_fetch\_absolute\(a\_sqlany\_stmt \*, sacapi\_i32\) Method](sqlany-fetch-absolute-a-sqlany-stmt-sacapi-i32-method-3bf5955.md "Moves the current row in the result set to the specified row number and then fetches rows of data starting from the current row.")

[sqlany\_fetch\_next\(a\_sqlany\_stmt \*\) Method](sqlany-fetch-next-a-sqlany-stmt-method-3bf59e2.md "Returns the next set of rows from the result set.")

[sqlany\_set\_rowset\_pos\(a\_sqlany\_stmt \*, sacapi\_u32\) Method](sqlany-set-rowset-pos-a-sqlany-stmt-sacapi-u32-method-9d058ac.md "Sets the current row in the fetched row set.")

