<!-- loio9cf5d420a7d31014822bbb48b7d8524b -->

# sqlany\_bind\_column\(a\_sqlany\_stmt \*, sacapi\_u32, a\_sqlany\_data\_value \*\) Method

Binds a user-supplied buffer as a result set column to the prepared statement.



```
public sacapi_bool sqlany_bind_column (
    a_sqlany_stmt * sqlany_stmt,
    sacapi_u32 index,
    a_sqlany_data_value * value
)
```



## Parameters

sqlany\_stmt
:   A statement prepared successfully using sqlany\_prepare\(\).

index
:   The index of the column. This number must be between 0 and sqlany\_num\_cols\(\) - 1.

value
:   An a\_sqlany\_data\_value structure describing the bound buffers, or NULL to clear previous binding information.



## Returns

1 on success or 0 on unsuccessful.



## Remarks

If the size of the fetched row set is greater than 1, the buffer must be large enough to hold the data of all of the rows in the row set. This function can also be used to clear the binding of a column by specifying value to be NULL.

**Related Information**  


[sqlany\_clear\_column\_bindings\(a\_sqlany\_stmt \*\) Method](sqlany-clear-column-bindings-a-sqlany-stmt-method-9cf72b8.md "Removes all column bindings defined using sqlany_bind_column().")

[sqlany\_set\_rowset\_size\(a\_sqlany\_stmt \*, sacapi\_u32\) Method](sqlany-set-rowset-size-a-sqlany-stmt-sacapi-u32-method-9d0617f.md "Sets the size of the row set to be fetched by the sqlany_fetch_absolute() and sqlany_fetch_next() functions.")

