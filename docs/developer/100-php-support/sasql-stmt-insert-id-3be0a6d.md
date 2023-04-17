<!-- loio3be0a6d46c5f10149249e54e933020fb -->

# sasql\_stmt\_insert\_id

Returns the last value inserted into an IDENTITY column or a DEFAULT AUTOINCREMENT column, or zero if the most recent insert was into a table that did not contain an IDENTITY or DEFAULT AUTOINCREMENT column.



```
int sasql_stmt_insert_id( sasql_stmt <$stmt> )
```



## Parameters

$stmt
:   A statement resource that was executed by sasql\_stmt\_execute.



## Returns

The ID generated for an IDENTITY column or a DEFAULT AUTOINCREMENT column by a previous INSERT statement, or zero if the last insert did not affect an IDENTITY or DEFAULT AUTOINCREMENT column. The function can return FALSE \(0\) if $stmt is not valid.

