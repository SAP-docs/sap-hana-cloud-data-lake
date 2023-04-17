<!-- loioa55ea65684f21015a60794ef54777c14 -->

# LENGTH Function \[String\] for Data Lake Relational Engine

Returns the number of characters in the specified string.



```
LENGTH ( <string-expression> )
```



<a name="loioa55ea65684f21015a60794ef54777c14__LENGTH_parm1"/>

## Parameters

 *<string-expression\>*
 :   The string.

 

<a name="loioa55ea65684f21015a60794ef54777c14__LENGTH_returns1"/>

## Returns

INT



<a name="loioa55ea65684f21015a60794ef54777c14__LENGTH_remarks1"/>

## Remarks

If the string contains multibyte characters, and the proper collation is being used, LENGTH returns the number of characters, not the number of bytes. If the string is of BINARY data type, the LENGTH function behaves as BYTE\_LENGTH.

The LENGTH function is the same as the CHAR\_LENGTH function.



<a name="loioa55ea65684f21015a60794ef54777c14__LENGTH_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa55ea65684f21015a60794ef54777c14__LENGTH_example1"/>

## Example

The following statement returns the value 9:

```
SELECT LENGTH( 'chocolate' ) FROM iq_dummy
```

**Related Information**  


[String Functions in Data Lake Relational Engine](string-functions-in-data-lake-relational-engine-a52d1d9.md "String functions perform conversion, extraction, or manipulation operations on strings, or return information about strings.")

[LENGTH Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/ae555cf86ee34fe887637dbcd64a33c3.html "Returns the number of characters in the specified string.") :arrow_upper_right:

