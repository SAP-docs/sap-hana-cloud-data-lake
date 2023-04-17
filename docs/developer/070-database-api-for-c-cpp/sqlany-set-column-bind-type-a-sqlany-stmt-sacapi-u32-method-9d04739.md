<!-- loio9d04739ba7d31014ac41c7a9ce719291 -->

# sqlany\_set\_column\_bind\_type\(a\_sqlany\_stmt \*, sacapi\_u32\) Method

Sets the bind type of columns.



```
public sacapi_bool sqlany_set_column_bind_type (
    a_sqlany_stmt * sqlany_stmt,
    sacapi_u32 row_size
)
```



## Parameters

sqlany\_stmt
:   A statement prepared successfully using sqlany\_prepare\(\).

row\_size
:   The byte size of the row. A value of 0 indicates column-wise binding and a positive value indicates row-wise binding.



## Returns

1 on success or 0 on failure.



## Remarks

The default value is 0, which indicates column-wise binding. A non-zero value indicates row-wise binding and specifies the byte size of the data structure that stores the row. The column is bound to the first element in a contiguous array of values. The address offset to the next element is computed based on the bind type:

-   Column-wise binding - the byte size of the column type
-   Row-wise binding - the row\_size

**Related Information**  


[sqlany\_bind\_column\(a\_sqlany\_stmt \*, sacapi\_u32, a\_sqlany\_data\_value \*\) Method](sqlany-bind-column-a-sqlany-stmt-sacapi-u32-a-sqlany-data-value-method-9cf5d42.md "Binds a user-supplied buffer as a result set column to the prepared statement.")

