<!-- loio3bdeeddd6c5f10149ed682b02549cb71 -->

# sasql\_affected\_rows

Returns the number of rows affected by the last SQL statement.



```
int sasql_affected_rows( sasql_conn <$conn> )
```



## Parameters

$conn
:   The connection resource returned by a connect function.



## Returns

The number of rows affected.



## Remarks

This function is typically used for INSERT, UPDATE, or DELETE statements. For SELECT statements, use the sasql\_num\_rows function.

