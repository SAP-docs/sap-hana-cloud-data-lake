<!-- loio9d04f6d2a7d310148c5c9d39185b0373 -->

# sqlany\_set\_param\_bind\_type\(a\_sqlany\_stmt \*, size\_t\) Method

Sets the bind type of parameters.



```
public sacapi_bool sqlany_set_param_bind_type (
    a_sqlany_stmt * sqlany_stmt,
    size_t row_size
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

The default value is 0, which indicates column-wise binding. A non-zero value indicates row-wise binding and specifies the byte size of the data structure that stores the row. The parameter is bound to the first element in a contiguous array of values. The address offset to the next element is computed based on the bind type:

-   Column-wise binding - the byte size of the parameter type
-   Row-wise binding - the row\_size

**Related Information**  


[sqlany\_bind\_param\(a\_sqlany\_stmt \*, sacapi\_u32, a\_sqlany\_bind\_param \*\) Method](sqlany-bind-param-a-sqlany-stmt-sacapi-u32-a-sqlany-bind-param-method-3bf5173.md "Bind a user-supplied buffer as a parameter to the prepared statement.")

