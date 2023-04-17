<!-- loioa55fae8484f2101591b6b7d46dca7cc4 -->

# LOCATE Function \[String\] for Data Lake Relational Engine

Returns the position of one string within another.



```
LOCATE ( <string-expression1>, <string-expression2>
[ , <numeric-expression> ] )
```



<a name="loioa55fae8484f2101591b6b7d46dca7cc4__LOCATE_parm1"/>

## Parameters

 *<string-expression1\>*
 :   The string to be searched.

  *<string-expression2\>*
 :   The string for which you are searching. This string is limited to 255 bytes.

  *<numeric-expression\>*
 :   The character position in the string to begin the search. The first character is position 1. If the starting offset is negative, the locate function returns the last matching string offset rather than the first. A negative offset indicates how much of the end of the string is to be excluded from the search. The number of bytes excluded is calculated as \(-1 \* offset\) -1.

    The *<numeric-expression\>* is a 32 bit signed integer for CHAR, VARCHAR, and BINARY columns.

    If *<numeric-expression\>* is specified, the search starts at that offset into the string being searched.

    If *<numeric-expression\>* is not specified, LOCATE returns only the position of the first instance of the specified string.

 

<a name="loioa55fae8484f2101591b6b7d46dca7cc4__LOCATE_returns1"/>

## Returns

INT



<a name="loioa55fae8484f2101591b6b7d46dca7cc4__LOCATE_remarks1"/>

## Remarks

The first string can be a long string \(longer than 255 bytes\), but the second is limited to 255 bytes. A second string longer than 255 bytes causes an error.

If any of the arguments is NULL, the result is NULL.

Searching for a zero-length string returns 1.

If the string does not contain the specified string, the LOCATE function returns zero \(0\).

All the positions or offsets, returned or specified, in the LOCATE function are always character offsets and may be different from the byte offset for multibyte data.

If arguments *<string-expression-1\>* and *<string-expression-2\>* are of binary data type, the `LOCATE` function behaves the same as the BYTE\_LOCATE function.



<a name="loioa55fae8484f2101591b6b7d46dca7cc4__LOCATE_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa55fae8484f2101591b6b7d46dca7cc4__LOCATE_examples1"/>

## Examples

-   The following statement returns the value 8:

    ```
    SELECT LOCATE( 'office party this week – rsvp as soon as possible', 'party', 2 ) FROM iq_dummy
    ```

-   In the second example, the *<numeric-expression\>* starting offset for the search is a negative number:

    ```
    CREATE TABLE t1(name VARCHAR(20), dirname VARCHAR(60));
      INSERT INTO t1     VALUES(‘m1000’,’c:\test\functions\locate.sql’);
      INSERT INTO t1     VALUES(‘m1001’,’d:\test\functions\trim.sql’);
    COMMIT;
    
    SELECT LOCATE(dirname, ‘\’, -1), dirname FROM t1;
    ```

    The result is:

    ```
    18   c:\test\functions\locate.sql
    18   d:\test\functions\trim.sql
    ```


**Related Information**  


[LIKE Conditions](../010-sql-language-elements/like-conditions-a4fd6d2.md "Use LIKE conditions in subqueries to use wildcards in the WHERE clause to perform pattern matching.")

[PATINDEX Function \[String\] for Data Lake Relational Engine](patindex-function-string-for-data-lake-relational-engine-a56c8f8.md "Returns the starting position of the first occurrence of a specified pattern.")

[LOCATE Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/ea53f0bcd5e34cc8a53d2c6ea32d5b5c.html "Returns the position of one string within another.") :arrow_upper_right:

