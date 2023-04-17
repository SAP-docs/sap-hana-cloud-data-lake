<!-- loio3bf5f4516c5f1014829e8df637745c65 -->

# sqlany\_get\_bind\_param\_info\(a\_sqlany\_stmt \*, sacapi\_u32, a\_sqlany\_bind\_param\_info \*\) Method

Retrieves information about the parameters that were bound using sqlany\_bind\_param\(\).



```
public sacapi_bool sqlany_get_bind_param_info (
    a_sqlany_stmt * sqlany_stmt,
    sacapi_u32 index,
    a_sqlany_bind_param_info * info
)
```



## Parameters

sqlany\_stmt
:   A statement prepared successfully using sqlany\_prepare\(\).

index
:   The index of the parameter. This number should be between 0 and sqlany\_num\_params\(\) - 1.

info
:   A sqlany\_bind\_param\_info buffer to be populated with the bound parameter's information.



## Returns

1 on success or 0 on failure.

**Related Information**  


[sqlany\_bind\_param\(a\_sqlany\_stmt \*, sacapi\_u32, a\_sqlany\_bind\_param \*\) Method](sqlany-bind-param-a-sqlany-stmt-sacapi-u32-a-sqlany-bind-param-method-3bf5173.md "Bind a user-supplied buffer as a parameter to the prepared statement.")

[sqlany\_describe\_bind\_param\(a\_sqlany\_stmt \*, sacapi\_u32, a\_sqlany\_bind\_param \*\) Method](sqlany-describe-bind-param-a-sqlany-stmt-sacapi-u32-a-sqlany-bind-param-method-3bf55c0.md "Describes the bind parameters of a prepared statement.")

[sqlany\_prepare\(a\_sqlany\_connection \*, const char \*\) Method](sqlany-prepare-a-sqlany-connection-const-char-method-3bf6a1b.md "Prepares a supplied SQL string.")

