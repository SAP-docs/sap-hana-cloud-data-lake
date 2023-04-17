<!-- loio3be0bf6b6c5f101495dffff163240a68 -->

# sasql\_stmt\_param\_count

Returns the number of parameters in the supplied prepared statement resource.



```
int sasql_stmt_param_count( sasql_stmt <$stmt> )
```



## Parameters

$stmt
:   A statement resource returned by the sasql\_prepare function.



## Returns

The number of parameters or FALSE on error.

