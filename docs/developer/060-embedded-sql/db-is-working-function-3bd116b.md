<!-- loio3bd116ba6c5f1014ad3aebfadbc0903a -->

# db\_is\_working Function

Indicates whether a database request is in progress.



```
unsigned short db_is_working( SQLCA * <sqlca> );
```



## Parameters

sqlca
:   A pointer to a SQLCA structure.



## Returns

1 if your application has a database request in progress that uses the given *<sqlca\>* and 0 if there is no request in progress that uses the given *<sqlca\>*.



## Remarks

This function can be called asynchronously. This function and db\_cancel\_request are the only functions in the database interface library that can be called asynchronously using a SQLCA that might be in use by another request.

