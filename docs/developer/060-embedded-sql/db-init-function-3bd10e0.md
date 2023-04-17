<!-- loio3bd10e0a6c5f1014a20da0cc73d4d466 -->

# db\_init Function

Initialize the database interface library.



```
int db_init( SQLCA * <sqlca> );
```



## Parameters

sqlca
:   A pointer to a SQLCA structure.



## Returns

Non-zero value if successful; 0 otherwise.



## Remarks

This function initializes the database interface library. This function must be called before any other library call is made and before any Embedded SQL statement is executed. The resources the interface library required for your program are allocated and initialized on this call.

Use db\_fini to free the resources at the end of your program. If there are any errors during processing, they are returned in the SQLCA and 0 is returned. If there are no errors, a non-zero value is returned and you can begin using Embedded SQL statements and functions.

Usually, this function should be called only once \(passing the address of the global sqlca variable defined in the `sqlca.h` header file\). If you are writing a DLL or an application that has multiple threads using Embedded SQL, call db\_init once for each SQLCA that is being used.

