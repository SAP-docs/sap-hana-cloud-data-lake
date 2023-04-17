<!-- loio3bdf253f6c5f1014a2bbe53bf3b5f7dc -->

# sasql\_errorcode

Returns the error code of the most-recently executed function.



```
int sasql_errorcode( [ sasql_conn <$conn> ] )
```



## Parameters

$conn
:   The connection resource returned by a connect function.



## Returns

A signed integer representing an error code. An error code of 0 means success. A positive error code indicates success with warnings. A negative error code indicates failure.



## Remarks

Error codes are stored per connection. If no *<$conn\>* is specified, then sasql\_errorcode returns the last error code where no connection was available. For example, if you are calling sasql\_connect and the connection fails, then call sasql\_errorcode with no parameter for the *<$conn\>* to get the error code. To get the corresponding error message use the sasql\_error function.

