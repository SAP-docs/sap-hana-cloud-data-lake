<!-- loio3bdff53f6c5f1014b1d9a26b00bb13da -->

# sasql\_rollback

Ends a transaction on the database and discards any changes made during the transaction.



```
bool sasql_rollback( sasql_conn <$conn> )
```



## Parameters

$conn
:   The connection resource returned by a connect function.



## Returns

TRUE on success or FALSE on failure.



## Remarks

This function is only useful when the auto\_commit option is Off.

