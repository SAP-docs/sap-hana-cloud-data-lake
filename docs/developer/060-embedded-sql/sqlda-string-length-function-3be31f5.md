<!-- loio3be31f5a6c5f1014bae3f01174ebec7e -->

# sqlda\_string\_length Function

Determine the amount of storage required to store a value as a C string.



```
a_sql_uint32 sqlda_string_length( struct sqlda * <sqlda>, int <varno> );
```



## Parameters

 sqlda
 :   A pointer to a SQLDA structure.

  varno
 :   An index for a sqlvar host variable.

 

## Returns

An unsigned 32-bit integer value representing the length of the C string \(type DT\_STRING\) that would be required to hold the variable sqlda-\>sqlvar\[varno\] \(no matter what its type is\). It includes the null termination character.



In this example, all columns will be fetched as C strings \(DT\_STRING\). Since sqlda\_string\_length includes the null termination character, the sqllen field is set to exclude this character. The new sqltype must be set after the call to sqlda\_string\_length.

```
for( col = 0; col < sqlda->sqld; col++ ) {
    sqlda->sqlvar[col].sqllen = sqlda_string_length( sqlda, col ) - 1;
    sqlda->sqlvar[col].sqltype = DT_STRING;
}
fill_sqlda( sqlda );
```

