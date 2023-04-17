<!-- loio3be3164d6c5f10149e07ea100fe75b69 -->

# sqlda\_storage Function

Determine the amount of storage required to store a value.



```
a_sql_uint32 sqlda_storage( struct sqlda * <sqlda>, int <varno> );
```



## Parameters

 sqlda
 :   A pointer to a SQLDA structure.

  varno
 :   An index for a sqlvar host variable, starting at 0.

 

## Returns

An unsigned 32-bit integer value representing the amount of storage required to store any value for the variable described in sqlda-\>sqlvar\[varno\]. For example, this includes the null-termination characters for DT\_STRING and DT\_NSTRING, as well as the overhead for types such as DT\_VARCHAR, DT\_BINARY, DT\_LONGVARCHAR, DT\_LONGNVARCHAR, and so on. The calculation uses the current sqlda-\>sqlvar\[varno\].sqllen field value which is at most 32767.



## Remarks

For some types, there are also macros defined in the `sqlca.h` and `sqlda.h` header files that return the amount of storage required to store a variable of the indicated size. Since sqlda\_storage performs calculation based on the sqllen value which is limited to 32767, the macros for DT\_LONGBINARY, DT\_LONGVARCHAR, and DT\_LONGNVARCHAR may be more appropriate for larger sizes.

 \_BINARYSIZE\( n \)
 :   Returns the amount of storage required to store a DT\_BINARY of the specified length. Use the BINARY struct to map this storage.

  \_VARCHARSIZE\( n \)
 :   Returns the amount of storage required to store a DT\_VARCHAR of the specified length. Use the VARCHAR struct to map this storage.

  DECIMALSTORAGE\( n \)
 :   Returns the amount of storage required to store a DT\_DECIMAL of the specified length. Use the TYPE\_DECIMAL struct to map this storage.

  LONGBINARYSIZE\( n \)
 :   Returns the amount of storage required to store a DT\_LONGBINARY of the specified length. Use the LONGBINARY struct to map this storage.

  LONGNVARCHARSIZE\( n \)
 :   Returns the amount of storage required to store a DT\_LONGNVARCHAR of the specified length. Use the LONGNVARCHAR struct to map this storage.

  LONGVARCHARSIZE\( n \)
 :   Returns the amount of storage required to store a DT\_LONGVARCHAR of the specified length. Use the LONGVARCHAR struct to map this storage.

 These can be used to determine how much storage to allocate for a variable.



The following C code fragment allocates a 128K buffer for a DT\_LONGVARCHAR and initializes the three headers on this buffer:

```
    LONGVARCHAR *lvc;
    int          maxlen = 128*1024;

    lvc = (LONGVARCHAR *)DBAlloc( LONGVARCHARSIZE( maxlen ) );
    if( lvc ) 
    {
        lvc->array_len = maxlen;
        lvc->stored_len = 0;
        lvc->untrunc_len = 0;
    }

```

