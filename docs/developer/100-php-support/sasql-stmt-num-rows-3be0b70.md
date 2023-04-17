<!-- loio3be0b70d6c5f10148f499a2e5ba00973 -->

# sasql\_stmt\_num\_rows

Returns the number of rows in the result set.



```
int sasql_stmt_num_rows( sasql_stmt <$stmt> )
```



## Parameters

$stmt
:   A statement resource that was executed by sasql\_stmt\_execute and for which sasql\_stmt\_store\_result was called.



## Returns

The number of rows available in the result or 0 on failure.



## Remarks

The actual number of rows in the result set can only be determined after the sasql\_stmt\_store\_result function is called to buffer the entire result set. If the sasql\_stmt\_store\_result function has not been called, 0 is returned.

