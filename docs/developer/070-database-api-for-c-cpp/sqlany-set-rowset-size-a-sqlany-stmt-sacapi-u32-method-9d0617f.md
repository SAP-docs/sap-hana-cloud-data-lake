<!-- loio9d0617fea7d310148c51d67091314444 -->

# sqlany\_set\_rowset\_size\(a\_sqlany\_stmt \*, sacapi\_u32\) Method

Sets the size of the row set to be fetched by the sqlany\_fetch\_absolute\(\) and sqlany\_fetch\_next\(\) functions.



```
public sacapi_bool sqlany_set_rowset_size (
    a_sqlany_stmt * sqlany_stmt,
    sacapi_u32 num_rows
)
```



## Parameters

sqlany\_stmt
:   A statement prepared successfully using sqlany\_prepare\(\).

num\_rows
:   The size of the row set. The value must be 1 or greater.



## Returns

1 on success or 0 on failure.



## Remarks

The default size of the row set is 1. Specifying num\_rows to be a value greater than 1 indicates a wide fetch.

**Related Information**  


[sqlany\_bind\_column\(a\_sqlany\_stmt \*, sacapi\_u32, a\_sqlany\_data\_value \*\) Method](sqlany-bind-column-a-sqlany-stmt-sacapi-u32-a-sqlany-data-value-method-9cf5d42.md "Binds a user-supplied buffer as a result set column to the prepared statement.")

[sqlany\_fetch\_absolute\(a\_sqlany\_stmt \*, sacapi\_i32\) Method](sqlany-fetch-absolute-a-sqlany-stmt-sacapi-i32-method-3bf5955.md "Moves the current row in the result set to the specified row number and then fetches rows of data starting from the current row.")

[sqlany\_fetch\_next\(a\_sqlany\_stmt \*\) Method](sqlany-fetch-next-a-sqlany-stmt-method-3bf59e2.md "Returns the next set of rows from the result set.")

[sqlany\_get\_rowset\_size\(a\_sqlany\_stmt \*\) Method](sqlany-get-rowset-size-a-sqlany-stmt-method-9cff5a5.md "Retrieves the size of the row set to be fetched by the sqlany_fetch_absolute() and sqlany_fetch_next() functions.")

