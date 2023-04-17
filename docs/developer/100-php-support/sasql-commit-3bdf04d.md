<!-- loio3bdf04db6c5f1014984d9998dafd6e69 -->

# sasql\_commit

Ends a transaction on the database and makes any changes made during the transaction permanent.



```
bool sasql_commit( sasql_conn <$conn> )
```



## Parameters

$conn
:   The connection resource returned by a connect function.



## Returns

TRUE on success or FALSE on failure.



## Remarks

Useful only when the auto\_commit option is Off.

