<!-- loio3be2feec6c5f10148aafa6820bb8e057 -->

# The SQL Communication Area \(SQLCA\)

The **SQL Communication Area** \(**SQLCA**\) is an area of memory that is used on every database request for communicating statistics and errors from the application to the database server and back to the application.

The SQLCA is used as a handle for the application-to-database communication link. It is passed in to all database library functions that must communicate with the database server. It is implicitly passed on all Embedded SQL statements.

A global SQLCA variable is defined in the interface library. The Embedded SQL preprocessor generates an external reference for the global SQLCA variable and an external reference for a pointer to it. The external reference is named sqlca and is of type SQLCA. The pointer is named sqlcaptr. The actual global variable is declared in the import library.

The SQLCA is defined by the `sqlca.h` header file, included in the `SDK\Include` subdirectory of your software installation directory.



## SQLCA Provides Error Codes

You reference the SQLCA to test for a particular error code. The sqlcode and sqlstate fields contain error codes when a database request has an error. Some C macros are defined for referencing the sqlcode field, the sqlstate field, and some other fields.

