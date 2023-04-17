<!-- loio3be06a5a6c5f1014963dfbb1290c7525 -->

# sasql\_stmt\_data\_seek

Seeks to the specified offset in the result set.



```
bool sasql_stmt_data_seek( sasql_stmt <$stmt>, int <$offset> )
```



## Parameters

$stmt
:   A statement resource.

$offset
:   The offset in the result set. This is a number between 0 and \(sasql\_stmt\_num\_rows\($stmt\) - 1\).



## Returns

TRUE on success or FALSE failure.

