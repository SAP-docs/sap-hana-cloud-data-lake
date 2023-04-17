<!-- loio3be061036c5f10148b7bc65b2c173be6 -->

# sasql\_stmt\_close

Closes the supplied statement resource and frees any resources associated with it.



```
bool sasql_stmt_close( sasql_stmt <$stmt> )
```



## Parameters

$stmt
:   A prepared statement resource that was returned by the sasql\_prepare function.



## Returns

TRUE for success or FALSE on failure.



## Remarks

This function will also free any result objects that were returned by the sasql\_stmt\_result\_metadata.

