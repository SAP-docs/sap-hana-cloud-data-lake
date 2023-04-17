<!-- loio3bd0fe306c5f1014b5f585e53e63f802 -->

# db\_fini Function

Free resources used by the database interface or DLL.



```
int db_fini( SQLCA * <sqlca> );
```



## Parameters

sqlca
:   A pointer to a SQLCA structure.



## Returns

Non-zero value for success; 0 otherwise.



## Remarks

This function frees resources used by the database interface or DLL. You must not make any other library calls or execute any Embedded SQL statements after db\_fini is called. If an error occurs during processing, the error code is set in SQLCA and the function returns 0. If there are no errors, a non-zero value is returned.

You must call db\_fini once for each SQLCA being used.

The db\_fini function should not be called directly or indirectly from the DllMain function in a Windows Dynamic Link Library. The DllMain entry point function is intended to perform only simple initialization and termination tasks. Calling db\_fini can create deadlocks and circular dependencies.

