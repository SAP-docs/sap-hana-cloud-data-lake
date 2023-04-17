<!-- loio3be0332b6c5f1014ada785e6001ceae3 -->

# sasql\_sqlstate

Returns the most recent SQLSTATE string.



```
string sasql_sqlstate( sasql_conn <$conn> )
```



## Parameters

$conn
:   The connection resource returned by a connect function.



## Returns

Returns a string of five characters containing the current SQLSTATE code. The result "00000" means no error.



## Remarks

SQLSTATE indicates whether the most recently executed SQL statement resulted in a success, error, or warning condition. SQLSTATE codes consists of five characters with "00000" representing no error. The values are defined by the ISO/ANSI SQL standard.

