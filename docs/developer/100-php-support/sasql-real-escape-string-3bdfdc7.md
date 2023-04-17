<!-- loio3bdfdc7e6c5f10149eeaa15790207c25 -->

# sasql\_real\_escape\_string

Escapes all special characters in the supplied string.



```
string sasql_real_escape_string( sasql_conn <$conn>, string <$str> )
```



## Parameters

$conn
:   The connection resource returned by a connect function.

$string
:   The string to be escaped.



## Returns

The escaped string or FALSE on error.



## Remarks

The special characters that are escaped are \\r, \\n, ', ", ;, \\, and the NULL character.

