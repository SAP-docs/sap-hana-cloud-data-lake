<!-- loioa4bc624684f210158651b7c4f69cf381 -->

# Open Client and jConnect Connections

When data lake Relational Engine serves applications over TDS, it automatically sets relevant database options to values that are compatible with SAP SQL Anywhere Server default behavior. These options are set temporarily, for the duration of the connection only. The client application can override these options at any time.

> ### Note:  
> Data lake Relational Engine does not support the `ANSI_BLANKS`, `FLOAT_AS_DOUBLE`, and `TSQL_HEX_CONSTANT`options.

Although data lake Relational Engine allows longer user names and passwords, TDS client user names and passwords cannot exceed 30 bytes. If your password or user ID is longer than 30 bytes, attempts to connect over TDS \(for example, using jConnect\) return an ***Invalid user ID or password*** error.

> ### Note:  
> ODBC applications, including Interactive SQL applications, automatically set certain database options to values mandated by the ODBC specification. This overwrites settings by the `LOGIN_PROCEDURE` database option.

