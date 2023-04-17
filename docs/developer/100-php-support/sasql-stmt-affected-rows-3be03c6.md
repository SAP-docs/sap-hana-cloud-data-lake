<!-- loio3be03c6b6c5f1014a790e00e180ab1b0 -->

# sasql\_stmt\_affected\_rows

Returns the number of rows affected by executing the statement.



```
int sasql_stmt_affected_rows( sasql_stmt <$stmt> )
```



## Parameters

$stmt
:   A statement resource that was executed by sasql\_stmt\_execute.



## Returns

The number of rows affected or FALSE on failure.

