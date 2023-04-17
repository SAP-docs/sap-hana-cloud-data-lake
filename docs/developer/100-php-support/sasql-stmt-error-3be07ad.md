<!-- loio3be07ad96c5f1014b42ed4b977c8ec8a -->

# sasql\_stmt\_error

Returns the error text for the most recently executed statement function using the specified statement resource.



```
string sasql_stmt_error( sasql_stmt <$stmt> )
```



## Parameters

$stmt
:   A prepared statement resource that was returned by the sasql\_prepare function.



## Returns

A string describing the error.

