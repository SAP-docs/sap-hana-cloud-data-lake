<!-- loio3bd39f0a6c5f1014a2bbf6f9232095c8 -->

# fill\_sqlda\_ex Function

Allocate space for each variable described in each descriptor of a SQLDA, with special processing for LONG data types.



```
struct sqlda * fill_sqlda_ex( struct sqlda * <sqlda> , unsigned int <flags> );
```



## Parameters

 sqlda
 :   A pointer to a SQLDA structure.

  flags
 :   0 or FILL\_SQLDA\_FLAG\_RETURN\_DT\_LONG

 

## Returns

 *<sqlda\>* if successful and returns NULL if there is not enough memory available.



## Remarks

Allocates space for each variable described in each descriptor of *<sqlda\>*, and assigns the address of this memory to the `sqldata` field of the corresponding descriptor. Enough space is allocated for the database type and length indicated in the descriptor.

For the DT\_STRING variable type, the `sqllen` is updated to include the null-terminator. DT\_STRING variables are always null-terminated. Other variable types are not null-terminated.

The SQLDA should be freed using the free\_filled\_sqlda function.

One flag bit is supported: FILL\_SQLDA\_FLAG\_RETURN\_DT\_LONG. This flag is defined in sqlca.h.

FILL\_SQLDA\_FLAG\_RETURN\_DT\_LONG preserves DT\_LONGVARCHAR, DT\_LONGNVARCHAR and DT\_LONGBINARY types in the filled descriptor. If this flag bit is not specified, fill\_sqlda\_ex converts DT\_LONGVARCHAR, DT\_LONGNVARCHAR and DT\_LONGBINARY types to DT\_VARCHAR, DT\_NVARCHAR and DT\_BINARY respectively. Using DT\_LONG... types makes it possible to fetch 32767 bytes, not the 32765 bytes that DT\_VARCHAR, DT\_NVARCHAR and DT\_BINARY are limited to.

fill\_sqlda\( sqlda \) is equivalent to fill\_sqlda\_ex\( sqlda, 0 \).

