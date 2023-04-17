<!-- loio3be0e0036c5f101499bb8675dc8ce210 -->

# sasql\_stmt\_store\_result

Allows the client to cache the whole result set of the statement.



```
bool sasql_stmt_store_result( sasql_stmt <$stmt> )
```



## Parameters

$stmt
:   A statement resource that was executed using sasql\_stmt\_execute.



## Returns

TRUE on success or FALSE on failure.



## Remarks

You can use the function sasql\_stmt\_free\_result to free the cached result.

