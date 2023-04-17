<!-- loio3be047096c5f10149c09f623aa401701 -->

# sasql\_stmt\_bind\_param\_ex

Binds a PHP variable to a statement parameter.



```
bool sasql_stmt_bind_param_ex( sasql_stmt <$stmt>, int <$param_number>, mixed &<$var>, string <$type> [, bool <$is_null> [, int <$direction> ] ] )
```



## Parameters

$stmt
:   A prepared statement resource that was returned by the sasql\_prepare function.

$param\_number
:   The parameter number. This should be a number between 0 and \(sasql\_stmt\_param\_count\($stmt\) - 1\).

$var
:   A PHP variable. Only references to PHP variables are allowed.

$type
:   Type of the variable. This can be one of: *s* for string, *i* for integer, *d* for double, *b* for blobs.

$is\_null
:   Whether the value of the variable is NULL or not.

$direction
:   Can be SASQL\_D\_INPUT, SASQL\_D\_OUTPUT, or SASQL\_INPUT\_OUTPUT.



## Returns

TRUE if binding the variable was successful or FALSE otherwise.

