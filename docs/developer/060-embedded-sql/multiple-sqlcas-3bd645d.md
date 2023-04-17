<!-- loio3bd645d06c5f10149435f7046055716b -->

# Multiple SQLCAs

You must not use the Embedded SQL preprocessor option \(-r-\) that generates non-reentrant code. Reentrant code is a little larger and a little slower because statically initialized global variables cannot be used. However, these effects are minimal.

Each SQLCA used in your program must be initialized with a call to db\_init and cleaned up at the end with a call to db\_fini.

The Embedded SQL statement SET SQLCA is used to tell the Embedded SQL preprocessor to use a different SQLCA for database requests. Usually, a statement such as `EXEC SQL SET SQLCA 'task_data->sqlca';` is used at the top of your program or in a header file to set the SQLCA reference to point at task specific data. Performance is unaffected because this statement does not generate any code. It changes the state within the preprocessor so that any reference to the SQLCA uses the given string.

Each thread must have its own SQLCA. This requirement also applies to code in a shared library \(in a DLL, for example\) that uses Embedded SQL and is called by more than one thread in your application.

You can use the multiple SQLCA support in any of the supported Embedded SQL environments, but it is only required in reentrant code.

You do not need to use multiple SQLCAs to connect to more than one database or have more than one connection to a single database.

Each SQLCA can have one unnamed connection. Each SQLCA has an active or current connection.

All operations on a given database connection must use the same SQLCA that was used when the connection was established.

> ### Note:  
> Operations on different connections are subject to the normal record locking mechanisms and may cause each other to block and possibly to deadlock.

