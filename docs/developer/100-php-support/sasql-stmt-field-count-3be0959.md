<!-- loio3be095936c5f1014982ebc2052cd4d84 -->

# sasql\_stmt\_field\_count

Returns the number of columns in the result set of the statement.



```
int sasql_stmt_field_count( sasql_stmt <$stmt> )
```



## Parameters

$stmt
:   A statement resource.



## Returns

The number of columns in the result of the statement. If the statement does not return a result, it returns 0.

