<!-- loio3be327856c5f10149995effcedfc8901 -->

# The SQL Descriptor Area \(SQLDA\)

The SQLDA \(SQL Descriptor Area\) is an interface structure that is used for dynamic SQL statements. The structure is used to pass information regarding host variables and SELECT statement results to and from the database. The SQLDA is defined in the header file `sqlda.h`.

There are functions in the database interface shared library or DLL that you can use to manage SQLDAs.

When host variables are used with static SQL statements, the preprocessor constructs a SQLDA for those host variables. It is this SQLDA that is actually passed to and from the database server.

