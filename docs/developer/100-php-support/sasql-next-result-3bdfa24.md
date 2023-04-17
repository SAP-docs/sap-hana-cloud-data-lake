<!-- loio3bdfa2416c5f1014801f890836d764f1 -->

# sasql\_next\_result

Prepares the next result set from the last executed query.



```
bool sasql_next_result( sasql_conn <$conn> )
```



## Parameters

$conn
:   The connection resource returned by a connect function.



## Returns

FALSE if there is no other result set to be retrieved. TRUE if there is another result to be retrieved. Call sasql\_use\_result or sasql\_store\_result to retrieve the next result set.



## Remarks

Prepares the next result set from the last query that executed on *<$conn\>*.

