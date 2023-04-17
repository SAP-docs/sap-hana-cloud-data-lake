<!-- loio3be2f5e26c5f101499c1907455d3c6be -->

# SQLCA Fields

The SQLCA is a structure with several fields.



These fields have the following meanings:

sqlcaid
:   An 8-byte character field that contains the string SQLCA as an identification of the SQLCA structure. This field helps in debugging when you are looking at memory contents.

sqlcabc
:   A 32-bit integer that contains the length of the SQLCA structure \(136 bytes\).

sqlcode
:   A 32-bit integer that specifies the error code when the database detects an error on a request. Definitions for the error codes can be found in the header file `sqlerr.h`. The error code is 0 \(zero\) for a successful operation, positive for a warning, and negative for an error.

sqlerrml
:   The length of the information in the sqlerrmc field.

sqlerrmc
:   Zero or more character strings to be inserted into an error message. Some error messages contain one or more placeholder strings \(*<%1\>*, *<%2\>*, ...\) that are replaced with the strings in this field.

    For example, if a `Table Not Found` error is generated, sqlerrmc contains the table name, which is inserted into the error message at the appropriate place.

sqlerrp
:   Reserved.

sqlerrd
:   A utility array of 32-bit integers.

sqlwarn
:   Reserved.

sqlstate
:   The SQLSTATE status value. The ANSI SQL standard defines this type of return value from a SQL statement in addition to the SQLCODE value. The SQLSTATE value is always a five-character null-terminated string, divided into a two-character class \(the first two characters\) and a three-character subclass. Each character can be a digit from 0 through 9 or an uppercase alphabetic character A through Z.

    Any class or subclass that begins with 0 through 4 or A through H is defined by the SQL standard; other classes and subclasses are implementation defined. The SQLSTATE value '00000' means that there has been no error or warning.



## sqlerror Array

The sqlerror field array has the following elements.

sqlerrd\[1\] \(SQLIOCOUNT\)
:   The actual number of input/output operations that were required to complete a statement.

    The database server does not set this number to zero for each statement. Your program can set this variable to zero before executing a sequence of statements. After the last statement, this number is the total number of input/output operations for the entire statement sequence.

sqlerrd\[2\] \(SQLCOUNT\)
:   The value of this field depends on which statement is being executed.

    INSERT, UPDATE, PUT, and DELETE statements
    :   The number of rows that were affected by the statement.

    OPEN and RESUME statements
    :   On a cursor OPEN or RESUME, this field is filled in with either the actual number of rows in the cursor \(a value greater than *or equal to* 0\) or an estimate thereof \(a negative number whose absolute value is the estimate\). It is the actual number of rows if the database server can compute it without counting the rows. The database can also be configured to always return the actual number of rows using the row\_counts option.

    FETCH cursor statement
    :   The SQLCOUNT field is filled if a SQLE\_NOTFOUND warning is returned. It contains the number of rows by which a FETCH RELATIVE or FETCH ABSOLUTE statement goes outside the range of possible cursor positions \(a cursor can be on a row, before the first row, or after the last row\). For a wide fetch, SQLCOUNT is the number of rows actually fetched, and is less than or equal to the number of rows requested. During a wide fetch, SQLE\_NOTFOUND is only set if no rows are returned.

        The value is 0 if the row was not found, but the position is valid, for example, executing FETCH RELATIVE 1 when positioned on the last row of a cursor. The value is positive if the attempted fetch was beyond the end of the cursor, and negative if the attempted fetch was before the beginning of the cursor.

    GET DATA statement
    :   The SQLCOUNT field holds the actual length of the value.

    DESCRIBE statement
    :   If the WITH VARIABLE RESULT clause is used to describe procedures that may have more than one result set, SQLCOUNT is set to one of the following values:

        0
        :   The result set may change: the procedure call should be described again following each OPEN statement.

        1
        :   The result set is fixed. No re-describing is required.

        For the SQLE\_SYNTAX\_ERROR syntax error, the field contains the approximate character position within the statement where the error was detected.

sqlerrd\[3\] \(SQLIOESTIMATE\)
:   The estimated number of input/output operations that are required to complete the statement. This field is given a value on an OPEN or EXPLAIN statement.

