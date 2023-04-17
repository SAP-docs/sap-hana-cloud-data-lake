<!-- loio3be0834c6c5f10148d01b7cb2b8fdc45 -->

# sasql\_stmt\_execute

Executes the prepared statement. The sasql\_stmt\_result\_metadata can be used to check whether the statement returns a result set.



```
bool sasql_stmt_execute( sasql_stmt <$stmt> )
```



## Parameters

$stmt
:   A prepared statement resource that was returned by the sasql\_prepare function. Variables should be bound before calling execute.



## Returns

TRUE for success or FALSE on failure.

