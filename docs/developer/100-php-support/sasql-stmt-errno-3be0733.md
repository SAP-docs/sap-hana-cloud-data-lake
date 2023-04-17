<!-- loio3be073366c5f101483f9f9491351874f -->

# sasql\_stmt\_errno

Returns the error code for the most recently executed statement function using the specified statement resource.



```
int sasql_stmt_errno( sasql_stmt <$stmt> )
```



## Parameters

$stmt
:   A prepared statement resource that was returned by the sasql\_prepare function.



## Returns

An integer error code.

