<!-- loio3bd3685a6c5f1014a83bb3c483f5ef74 -->

# Embedded SQL Statement Summary

All Embedded SQL statements must be preceded with EXEC SQL and end with a semicolon \(;\).



There are two groups of Embedded SQL statements. Standard SQL statements are used by simply placing them in a C program enclosed with EXEC SQL and a semicolon \(;\). CONNECT, DELETE, SELECT, SET, and UPDATE have additional formats only available in Embedded SQL. The additional formats fall into the second category of Embedded SQL specific statements.

Several SQL statements are specific to Embedded SQL and can only be used in a C program.

Standard data manipulation and data definition statements can be used from Embedded SQL applications. In addition, the following statements are specifically for Embedded SQL programming:

CLOSE statement \[ESQL\] \[SP\]
:   Close a cursor.

CONNECT statement \[ESQL\] \[Interactive SQL\]
:   Connect to the database.

DEALLOCATE DESCRIPTOR statement \[ESQL\]
:   Reclaim memory for a descriptor.

Declaration section \[ESQL\]
:   Declare host variables for database communication.

DECLARE CURSOR statement \[ESQL\] \[SP\]
:   Declare a cursor.

DELETE statement \(positioned\) \[ESQL\] \[SP\]
:   Delete the row at the current position in a cursor.

DESCRIBE statement \[ESQL\]
:   Describe the host variables for a particular SQL statement.

DISCONNECT statement \[ESQL\] \[Interactive SQL\]
:   Disconnect from database server.

DROP STATEMENT statement \[ESQL\]
:   Free resources used by a prepared statement.

EXECUTE statement \[ESQL\]
:   Execute a particular SQL statement.

EXPLAIN statement \[ESQL\]
:   Explain the optimization strategy for a particular cursor.

FETCH statement \[ESQL\] \[SP\]
:   Fetch a row from a cursor.

GET DATA statement \[ESQL\]
:   Fetch long values from a cursor.

GET DESCRIPTOR statement \[ESQL\]
:   Retrieve information about a variable in a SQLDA.

GET OPTION statement \[ESQL\]
:   Get the setting for a particular database option.

INCLUDE statement \[ESQL\]
:   Include a file for SQL preprocessing.

OPEN statement \[ESQL\] \[SP\]
:   Open a cursor.

PREPARE statement \[ESQL\]
:   Prepare a particular SQL statement.

PUT statement \[ESQL\]
:   Insert a row into a cursor.

SET CONNECTION statement \[Interactive SQL\] \[ESQL\]
:   Change active connection.

SET DESCRIPTOR statement \[ESQL\]
:   Describe the variables in a SQLDA and place data into the SQLDA.

SET SQLCA statement \[ESQL\]
:   Set SQLCA to something other than the default global one.

UPDATE \(positioned\) statement \[ESQL\] \[SP\]
:   Update the row at the current location of a cursor.

WHENEVER statement \[ESQL\]
:   Specify actions to occur on errors in SQL statements.

