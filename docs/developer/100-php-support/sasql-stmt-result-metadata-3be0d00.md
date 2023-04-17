<!-- loio3be0d0006c5f1014b335ca9e3283e164 -->

# sasql\_stmt\_result\_metadata

Returns a result set object for the supplied statement.



```
sasql_result sasql_stmt_result_metadata( sasql_stmt <$stmt> )
```



## Parameters

$stmt
:   A statement resource that was prepared and executed.



## Returns

sasql\_result object or FALSE if the statement does not return any results.

