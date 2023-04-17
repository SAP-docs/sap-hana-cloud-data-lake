<!-- loio3bd7ac5d6c5f10148137bc349a883855 -->

# Embedded SQL

SQL statements embedded in a C or C++ source file are referred to as Embedded SQL. A preprocessor translates these statements into calls to a runtime library. Embedded SQL is an ISO/ANSI and IBM standard.

Embedded SQL is portable to other databases and other environments, and is functionally equivalent in all operating environments. It is a comprehensive, low-level interface that provides all the functionality available in the product. Embedded SQL requires knowledge of C or C++ programming languages.



## Embedded SQL Applications

You can develop C or C++ applications that access the database server using the Embedded SQL interface.

Embedded SQL is a database programming interface for the C and C++ programming languages. It consists of SQL statements intermixed with \(embedded in\) C or C++ source code. These SQL statements are translated by a **Embedded SQL preprocessor** into C or C++ source code, which you then compile.

At runtime, Embedded SQL applications use an **interface library** called DBLIB to communicate with a database server. DBLIB is a dynamic link library \(**DLL**\) or shared object on most platforms.

-   On Windows operating systems, the interface library is <code>dblib<i>17</i>.dll</code>.

-   On Linux operating systems,the interface library is <code>libdblib<i>17</i>.so</code>


Two flavors of Embedded SQL are provided. Static Embedded SQL is simpler to use, but is less flexible than dynamic Embedded SQL.

