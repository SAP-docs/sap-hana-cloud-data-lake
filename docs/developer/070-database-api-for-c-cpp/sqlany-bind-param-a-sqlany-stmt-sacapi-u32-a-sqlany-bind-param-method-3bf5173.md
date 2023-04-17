<!-- loio3bf517326c5f1014be08b7b3c32dab0b -->

# sqlany\_bind\_param\(a\_sqlany\_stmt \*, sacapi\_u32, a\_sqlany\_bind\_param \*\) Method

Bind a user-supplied buffer as a parameter to the prepared statement.



```
public sacapi_bool sqlany_bind_param (
    a_sqlany_stmt * sqlany_stmt,
    sacapi_u32 index,
    a_sqlany_bind_param * param
)
```



## Parameters

sqlany\_stmt
:   A statement prepared successfully using sqlany\_prepare\(\).

index
:   The index of the parameter. This number must be between 0 and sqlany\_num\_params\(\) - 1.

param
:   An a\_sqlany\_bind\_param structure description of the parameter to be bound.



## Returns

1 on success or 0 on unsuccessful.

**Related Information**  


[sqlany\_describe\_bind\_param\(a\_sqlany\_stmt \*, sacapi\_u32, a\_sqlany\_bind\_param \*\) Method](sqlany-describe-bind-param-a-sqlany-stmt-sacapi-u32-a-sqlany-bind-param-method-3bf55c0.md "Describes the bind parameters of a prepared statement.")

