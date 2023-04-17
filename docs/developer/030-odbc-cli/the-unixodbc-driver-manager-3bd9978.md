<!-- loio3bd997896c5f10149314ba8a60b62f55 -->

# The unixODBC Driver Manager

Versions of the unixODBC release before version 2.2.14 have incorrectly implemented some aspects of the 64-bit ODBC specification as defined by Microsoft. These differences will cause problems when using the unixODBC driver manager with the 64-bit ODBC driver.

To avoid these problems, be aware of the differences. One of them is the definition of SQLLEN and SQLULEN. These are 64-bit types in the Microsoft 64-bit ODBC specification, and are expected to be 64-bit quantities by the 64-bit ODBC driver. Some implementations of unixODBC define these two types as 32-bit quantities and this will result in problems when interfacing to the 64-bit ODBC driver.

There are three things that you must do to avoid problems on 64-bit platforms.

1.  Instead of including the unixODBC headers like `sql.h` and `sqlext.h`, include the `unixodbc.h` header file. This will guarantee that you have the correct definitions for SQLLEN and SQLULEN. The header files in unixODBC 2.2.14 or later versions correct this problem.

2.  You must ensure that you have used the correct types for all parameters. Use of the correct header file and the strong type checking of your C/C++ compiler should help in this area. You must also ensure that you have used the correct types for all variables that are set by the ODBC driver indirectly through pointers.

3.  Do not use versions of the unixODBC driver manager before release 2.2.14. Link directly to the ODBC driver instead. For example, ensure that the libodbc shared object is linked to the ODBC driver shared object.

    ```
    libodbc.so.1 -> libdbodbc17_r.so.1
    ```

    Alternatively, you can use the driver manager included with the database server software on platforms where it is available.


