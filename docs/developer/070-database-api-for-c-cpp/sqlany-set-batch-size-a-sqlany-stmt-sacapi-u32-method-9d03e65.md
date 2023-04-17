<!-- loio9d03e65da7d31014bce4c3c442b5837b -->

# sqlany\_set\_batch\_size\(a\_sqlany\_stmt \*, sacapi\_u32\) Method

Sets the size of the row array for a batch execute.



```
public sacapi_bool sqlany_set_batch_size (
    a_sqlany_stmt * sqlany_stmt,
    sacapi_u32 num_rows
)
```



## Parameters

sqlany\_stmt
:   A statement prepared successfully using sqlany\_prepare\(\).

num\_rows
:   The number of rows for batch execution. The value must be 1 or greater.



## Returns

1 on success or 0 on failure.



## Remarks

The batch size is used only for an INSERT statement. The default batch size is 1. A value greater than 1 indicates a wide insert.

**Related Information**  


[sqlany\_bind\_param\(a\_sqlany\_stmt \*, sacapi\_u32, a\_sqlany\_bind\_param \*\) Method](sqlany-bind-param-a-sqlany-stmt-sacapi-u32-a-sqlany-bind-param-method-3bf5173.md "Bind a user-supplied buffer as a parameter to the prepared statement.")

[sqlany\_get\_batch\_size\(a\_sqlany\_stmt \*\) Method](sqlany-get-batch-size-a-sqlany-stmt-method-9cfd270.md "Retrieves the size of the row array for a batch execute.")

