<!-- loio3bdf34c26c5f101481b79c802ee31922 -->

# sasql\_escape\_string

Escapes all special characters in the supplied string.



```
string sasql_escape_string( sasql_conn <$conn>, string <$str> )
```



## Parameters

$conn
:   The connection resource returned by a connect function.

$string
:   The string to be escaped.



## Returns

The escaped string.



## Remarks

The special characters that are escaped are \\r, \\n, ', ", ;, \\, and the NULL character. This function is an alias of sasql\_real\_escape\_string.

