<!-- loio3be32f8c6c5f10149f5fe6147e77f2d0 -->

# sqlerror\_message Function

Obtain the error message text.



```
char * sqlerror_message( SQLCA * <sqlca>, char * <buffer>, int <max> );
```



## Parameters

sqlca
:   A pointer to a SQLCA structure.

buffer
:   The buffer in which to place the message \(up to *<max\>* characters\).

max
:   The maximum length of the buffer.



## Returns

A pointer to a string that contains an error message or NULL if no error was indicated.



## Remarks

Returns a pointer to a string that contains an error message. The error message contains text for the error code in the SQLCA. If no error was indicated, a null pointer is returned. The error message is placed in the buffer supplied, truncated to length *<max\>* if necessary.

