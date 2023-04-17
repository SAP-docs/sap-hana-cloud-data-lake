<!-- loio3bf61bb86c5f1014ac7ef678cfcdc681 -->

# sqlany\_get\_column\(a\_sqlany\_stmt \*, sacapi\_u32, a\_sqlany\_data\_value \*\) Method

Fills the supplied buffer with the value fetched for the specified column at the current row.



```
public sacapi_bool sqlany_get_column (
    a_sqlany_stmt * sqlany_stmt,
    sacapi_u32 col_index,
    a_sqlany_data_value * buffer
)
```



## Parameters

sqlany\_stmt
:   A statement object executed by sqlany\_execute\(\) or sqlany\_execute\_direct\(\).

col\_index
:   The number of the column to be retrieved. The column number is between 0 and sqlany\_num\_cols\(\) - 1.

buffer
:   An a\_sqlany\_data\_value object to be filled with the data fetched for column col\_index at the current row in the row set.



## Returns

1 on success or 0 for failure. A failure can happen if any of the parameters are invalid or if there is not enough memory to retrieve the full value from the SQL Anywhere database server.



## Remarks

When a sqlany\_fetch\_absolute\(\) or sqlany\_fetch\_next\(\) function is executed, a row set is created and the current row is set to be the first row in the row set. The current row is set using the sqlany\_set\_rowset\_pos\(\) function.

For A\_BINARY and A\_STRING \* data types, value-\>buffer points to an internal buffer associated with the result set. Do not rely upon or alter the content of the pointer buffer as it changes when a new row is fetched or when the result set object is freed. Users should copy the data out of those pointers into their own buffers.

The value-\>length field indicates the number of valid characters that value-\>buffer points to. The data returned in value-\>buffer is not null-terminated. This function fetches all the returned values from the SQL Anywhere database server. For example, if the column contains a blob, this function attempts to allocate enough memory to hold that value. If you do not want to allocate memory, use sqlany\_get\_data\(\) instead.

**Related Information**  


[sqlany\_execute\_direct\(a\_sqlany\_connection \*, const char \*\) Method](sqlany-execute-direct-a-sqlany-connection-const-char-method-3bf574d.md "Executes the SQL statement specified by the string argument and possibly returns a result set.")

[sqlany\_execute\(a\_sqlany\_stmt \*\) Method](sqlany-execute-a-sqlany-stmt-method-3bf58a8.md "Executes a prepared statement.")

[sqlany\_fetch\_absolute\(a\_sqlany\_stmt \*, sacapi\_i32\) Method](sqlany-fetch-absolute-a-sqlany-stmt-sacapi-i32-method-3bf5955.md "Moves the current row in the result set to the specified row number and then fetches rows of data starting from the current row.")

[sqlany\_fetch\_next\(a\_sqlany\_stmt \*\) Method](sqlany-fetch-next-a-sqlany-stmt-method-3bf59e2.md "Returns the next set of rows from the result set.")

[sqlany\_set\_rowset\_pos\(a\_sqlany\_stmt \*, sacapi\_u32\) Method](sqlany-set-rowset-pos-a-sqlany-stmt-sacapi-u32-method-9d058ac.md "Sets the current row in the fetched row set.")

