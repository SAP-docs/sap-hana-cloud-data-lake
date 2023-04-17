<!-- loio3bd5c1646c5f1014975a9619dcd00a70 -->

# Library Function Reference

The Embedded SQL preprocessor generates calls to functions in the interface library or DLL. In addition to the calls generated by the Embedded SQL preprocessor, a set of library functions is provided to make database operations easier to perform.



Prototypes for these functions are included by the EXEC SQL INCLUDE SQLCA statement.



## DLL Entry Points

The DLL entry points are the same except that the prototypes have a modifier appropriate for DLLs.

You can declare the entry points in a portable manner using \_esqlentry\_, which is defined in `sqlca.h`. On Windows platforms, it resolves to the value \_\_stdcall.
