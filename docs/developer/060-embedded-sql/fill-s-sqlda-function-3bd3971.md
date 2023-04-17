<!-- loio3bd3971a6c5f1014a53ace696cc454a4 -->

# fill\_s\_sqlda Function

Allocate space for each variable described in each descriptor of a SQLDA, changing all data types to DT\_STRING.



```
struct sqlda * fill_s_sqlda(
struct sqlda * <sqlda>,
unsigned int <maxlen> );
```



## Parameters

 sqlda
 :   A pointer to a SQLDA structure.

  maxlen
 :   The maximum number of bytes to allocate for the string.

 

## Returns

 *<sqlda\>* if successful and returns NULL if there is not enough memory available.



## Remarks

This function is the same as fill\_sqlda, except that it changes all the data types in *<sqlda\>* to type DT\_STRING. Enough space is allocated to hold the string representation of the type originally specified by the SQLDA, up to a maximum of *<maxlen\>* - 1 bytes. The address of this memory is assigned to the `sqldata` field of the corresponding descriptor. The maximum value for *<maxlen\>* is 32767.

For DT\_STRING variable types, the `sqllen` is updated to include the null-terminator.

The SQLDA should be freed using the free\_filled\_sqlda function.

