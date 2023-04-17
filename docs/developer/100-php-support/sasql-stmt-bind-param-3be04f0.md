<!-- loio3be04f0c6c5f1014ad34cfdbbd6dd0b4 -->

# sasql\_stmt\_bind\_param

Binds PHP variables to statement parameters.



```
bool sasql_stmt_bind_param( sasql_stmt <$stmt>, string <$types>, mixed &<$var_1> [, mixed &<$var_2> .. ] )
```



## Parameters

$stmt
:   A prepared statement resource that was returned by the sasql\_prepare function.

$types
:   A string that contains one or more characters specifying the types of the corresponding bind. This can be any of: *s* for string, *i* for integer, *d* for double, *b* for blobs. The length of the $types string must match the number of parameters that follow the $types parameter \($var\_1, $var\_2, ...\). The number of characters should also match the number of parameter markers \(question marks\) in the prepared statement.

$var\_n
:   The variable references.



## Returns

TRUE if binding the variables was successful or FALSE otherwise.

