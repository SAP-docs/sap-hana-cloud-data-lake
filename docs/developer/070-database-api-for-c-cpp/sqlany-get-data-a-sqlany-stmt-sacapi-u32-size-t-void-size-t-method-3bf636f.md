<!-- loio3bf636f66c5f1014bad7fc918878d662 -->

# sqlany\_get\_data\(a\_sqlany\_stmt \*, sacapi\_u32, size\_t, void \*, size\_t\) Method

Retrieves the data fetched for the specified column at the current row into the supplied buffer memory.



```
public sacapi_i32 sqlany_get_data (
    a_sqlany_stmt * sqlany_stmt,
    sacapi_u32 col_index,
    size_t offset,
    void * buffer,
    size_t size
)
```



## Parameters

sqlany\_stmt
:   A statement object executed by sqlany\_execute\(\) or sqlany\_execute\_direct\(\).

col\_index
:   The number of the column to be retrieved. The column number is between 0 and sqlany\_num\_cols\(\) - 1.

offset
:   The starting offset of the data to get.

buffer
:   A buffer to be filled with the contents of the column at the current row in the row set. The buffer pointer must be aligned correctly for the data type copied into it.

size
:   The size of the buffer in bytes. The function fails if you specify a size greater than 2^31 - 1.



## Returns

The number of bytes successfully copied into the supplied buffer. This number must not exceed 2^31 - 1. 0 indicates that no data remains to be copied. -1 indicates a failure.



## Remarks

When a sqlany\_fetch\_absolute\(\) or sqlany\_fetch\_next\(\) function is executed, a row set is created and the current row is set to be the first row in the row set. The current row is set using the sqlany\_set\_rowset\_pos\(\) function.

**Related Information**  


[sqlany\_execute\(a\_sqlany\_stmt \*\) Method](sqlany-execute-a-sqlany-stmt-method-3bf58a8.md "Executes a prepared statement.")

[sqlany\_execute\_direct\(a\_sqlany\_connection \*, const char \*\) Method](sqlany-execute-direct-a-sqlany-connection-const-char-method-3bf574d.md "Executes the SQL statement specified by the string argument and possibly returns a result set.")

[sqlany\_fetch\_absolute\(a\_sqlany\_stmt \*, sacapi\_i32\) Method](sqlany-fetch-absolute-a-sqlany-stmt-sacapi-i32-method-3bf5955.md "Moves the current row in the result set to the specified row number and then fetches rows of data starting from the current row.")

[sqlany\_fetch\_next\(a\_sqlany\_stmt \*\) Method](sqlany-fetch-next-a-sqlany-stmt-method-3bf59e2.md "Returns the next set of rows from the result set.")

[sqlany\_set\_rowset\_pos\(a\_sqlany\_stmt \*, sacapi\_u32\) Method](sqlany-set-rowset-pos-a-sqlany-stmt-sacapi-u32-method-9d058ac.md "Sets the current row in the fetched row set.")

