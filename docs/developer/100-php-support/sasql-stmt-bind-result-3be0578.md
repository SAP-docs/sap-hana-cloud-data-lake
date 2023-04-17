<!-- loio3be0578f6c5f1014ae61ffadb79daa4f -->

# sasql\_stmt\_bind\_result

Binds one or more PHP variables to result columns of a statement that was executed, and returns a result set.



```
bool sasql_stmt_bind_result( sasql_stmt <$stmt>, mixed &<$var1> [, mixed &<$var2> .. ] )
```



## Parameters

$stmt
:   A statement resource that was executed by sasql\_stmt\_execute.

$var1
:   References to PHP variables that are bound to result set columns returned by the sasql\_stmt\_fetch.



## Returns

TRUE on success or FALSE on failure.

