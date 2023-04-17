<!-- loio3be0ae916c5f1014be90aee0e1e19702 -->

# sasql\_stmt\_next\_result

Advances to the next result from the statement.



```
bool sasql_stmt_next_result( sasql_stmt <$stmt> )
```



## Parameters

$stmt
:   A statement resource.



## Returns

TRUE on success or FALSE failure.



## Remarks

If there is another result set, the currently cashed results are discarded and the associated result set object deleted \(as returned by sasql\_stmt\_result\_metadata\).

