<!-- loio3bd2e33f6c5f101495b8e171aa24a2bb -->

# Loading DBLIB Dynamically under Windows

Load DBLIB dynamically from your Embedded SQL application using the `esqldll.c` module in the `SDK\C` subdirectory of your software installation directory so that you do not need to link against the import library.



## Context

This task is an alternative to the usual technique of linking an application against a static import library for a Dynamic Link Library \(DLL\) that contains the required function definitions.

A similar task can be used to dynamically load DBLIB on UNIX and Linux platforms.



## Procedure

1.  Your application must call db\_init\_dll to load the DBLIB DLL, and must call db\_fini\_dll to free the DBLIB DLL. The db\_init\_dll call must be before any function in the database interface, and no function in the interface can be called after db\_fini\_dll.

    You must still call the db\_init and db\_fini library functions.

2.  You must include the `esqldll.h` header file before the EXEC SQL INCLUDE SQLCA statement or include `sqlca.h` in your Embedded SQL program. The `esqldll.h` header file includes `sqlca.h`.

3.  A SQL OS macro must be defined. The header file `sqlos.h`, which is included by `sqlca.h`, attempts to determine the appropriate macro and define it. However, certain combinations of platforms and compilers may cause this to fail. In this case, you must add a \#define to the top of this file, or make the definition using a compiler option. Define the \_SQL\_OS\_WINDOWS for all Windows operating systems.

4.  Compile `esqldll.c`.

5.  Instead of linking against the import library, link the object module `esqldll.obj` with your Embedded SQL application objects.




## Results

The DBLIB interface DLL loads dynamically when you run your Embedded SQL application.



You can find a sample program illustrating how to load the interface library dynamically in the <code><i>%IQDIRSAMP17%</i>\SQLAnywhere\ESQLDynamicLoad</code> directory. The source code is in `sample.sqc`.

The following example compiles and links `sample.sqc` with the code from `esqldll.c` on Windows.

```
sqlpp sample.sqc
cl sample.c %IQDIR17%\sdk\c\esqldll.c /I%IQDIR17%\sdk\include Advapi32.lib
```

