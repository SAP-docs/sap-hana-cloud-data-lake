<!-- loio3bd3a73a6c5f101498af9129d137f363 -->

# fill\_sqlda Function

Allocate space for each variable described in each descriptor of a SQLDA.



```
struct sqlda * fill_sqlda( struct sqlda * <sqlda> );
```



## Parameters

 sqlda
 :   A pointer to a SQLDA structure.

 

## Returns

 *<sqlda\>* if successful and returns NULL if there is not enough memory available.



## Remarks

Allocates space for each variable described in each descriptor of *<sqlda\>*, and assigns the address of this memory to the `sqldata` field of the corresponding descriptor. Enough space is allocated for the database type and length indicated in the descriptor.

fill\_sqlda converts DT\_LONGVARCHAR, DT\_LONGNVARCHAR and DT\_LONGBINARY types to DT\_VARCHAR, DT\_NVARCHAR and DT\_BINARY respectively.

For the DT\_STRING variable type, the `sqllen` is updated to include the null-terminator. DT\_STRING variables are always null-terminated. Other variable types are not null-terminated.

The SQLDA should be freed using the free\_filled\_sqlda function.

fill\_sqlda\( sqlda \) is equivalent to fill\_sqlda\_ex\( sqlda, 0 \).

