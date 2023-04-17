<!-- loio3bdf87cf6c5f10148d01b41e70641b2a -->

# sasql\_insert\_id

Returns the last value inserted into an IDENTITY column or a DEFAULT AUTOINCREMENT column, or zero if the most recent insert was into a table that did not contain an IDENTITY or DEFAULT AUTOINCREMENT column.



```
int sasql_insert_id( sasql_conn <$conn> )
```



## Parameters

$conn
:   The connection resource returned by a connect function.



## Returns

The ID generated for an AUTOINCREMENT column by a previous INSERT statement or zero if last insert did not affect an AUTOINCREMENT column. The function can return FALSE if the *<$conn\>* is not valid.



## Remarks

The sasql\_insert\_id function is provided for compatibility with MySQL databases.

