<!-- loio3be08c2e6c5f10148520bf0988167a7b -->

# sasql\_stmt\_fetch

Fetches one row out of the result for the statement and places the columns in the variables that were bound using sasql\_stmt\_bind\_result.



```
bool sasql_stmt_fetch( sasql_stmt <$stmt> )
```



## Parameters

$stmt
:   A statement resource.



## Returns

TRUE on success or FALSE on failure.

