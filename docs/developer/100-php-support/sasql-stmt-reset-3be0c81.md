<!-- loio3be0c81b6c5f1014ab89be36c2757191 -->

# sasql\_stmt\_reset

Resets the statement object to the state just after the describe.



```
bool sasql_stmt_reset( sasql_stmt <$stmt> )
```



## Parameters

$stmt
:   A statement resource.



## Returns

TRUE on success or FALSE on failure.



## Remarks

This function resets the *<$stmt\>* object to the state just after the describe. Any variables that were bound are unbound and any data sent using sasql\_stmt\_send\_long\_data are dropped.

