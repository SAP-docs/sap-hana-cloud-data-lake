<!-- loio3bf55c0d6c5f1014a205928a5479b824 -->

# sqlany\_describe\_bind\_param\(a\_sqlany\_stmt \*, sacapi\_u32, a\_sqlany\_bind\_param \*\) Method

Describes the bind parameters of a prepared statement.



```
public sacapi_bool sqlany_describe_bind_param (
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
 :   An a\_sqlany\_bind\_param structure that is populated with information.

 

## Returns

1 when successful or 0 when unsuccessful.



## Remarks

This function allows the caller to determine information about prepared statement parameters. The type of prepared statement, stored procedure, or DML statement determines the amount of information provided. The direction of the parameters \(input, output, or input-output\) are always provided.

**Related Information**  


[sqlany\_bind\_param\(a\_sqlany\_stmt \*, sacapi\_u32, a\_sqlany\_bind\_param \*\) Method](sqlany-bind-param-a-sqlany-stmt-sacapi-u32-a-sqlany-bind-param-method-3bf5173.md "Bind a user-supplied buffer as a parameter to the prepared statement.")

[sqlany\_prepare\(a\_sqlany\_connection \*, const char \*\) Method](sqlany-prepare-a-sqlany-connection-const-char-method-3bf6a1b.md "Prepares a supplied SQL string.")

