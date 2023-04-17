<!-- loio9cf72b8ca7d31014b495c16bea9b32a4 -->

# sqlany\_clear\_column\_bindings\(a\_sqlany\_stmt \*\) Method

Removes all column bindings defined using sqlany\_bind\_column\(\).



```
public sacapi_bool sqlany_clear_column_bindings (a_sqlany_stmt * sqlany_stmt)
```



## Parameters

sqlany\_stmt
:   A statement prepared successfully using sqlany\_prepare\(\).



## Returns

1 on success or 0 on failure.

**Related Information**  


[sqlany\_bind\_column\(a\_sqlany\_stmt \*, sacapi\_u32, a\_sqlany\_data\_value \*\) Method](sqlany-bind-column-a-sqlany-stmt-sacapi-u32-a-sqlany-data-value-method-9cf5d42.md "Binds a user-supplied buffer as a result set column to the prepared statement.")

