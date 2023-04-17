<!-- loioa53bd3d384f21015bcf88da636a1a768 -->

# CHAR\_LENGTH Function \[String\] for Data Lake Relational Engine

Returns the number of characters in a string.



```
CHAR_LENGTH ( <string-expression> )
```



<a name="loioa53bd3d384f21015bcf88da636a1a768__CHAR_LENGTH_parm1"/>

## Parameters

 *<string-expression\>*
 :   The string that has the length to be calculated.

 

<a name="loioa53bd3d384f21015bcf88da636a1a768__CHAR_LENGTH_returns1"/>

## Returns

INT



<a name="loioa53bd3d384f21015bcf88da636a1a768__CHAR_LENGTH_remarks1"/>

## Remarks

Trailing white space characters are included in the length returned.

The return value of a NULL string is NULL.

If the string is in a multibyte character set, the CHAR\_LENGTH value may be less than the BYTE\_LENGTH value.

CHAR\_LENGTH64 also supports LONG VARCHAR variables of any data size.

The CHAR\_LENGTH function supports LONG VARCHAR columns and LONG VARCHAR variables of any size of data. If the character length exceeds 2GB - 1 \(2147483647\), an error is returned.



<a name="loioa53bd3d384f21015bcf88da636a1a768__CHAR_LENGTH_standards1"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant



<a name="loioa53bd3d384f21015bcf88da636a1a768__CHAR_LENGTH_example1"/>

## Example

The following statement returns the value 8:

```
SELECT CHAR_LENGTH( 'Chemical' ) FROM iq_dummy
```

**Related Information**  


[String Functions in Data Lake Relational Engine](string-functions-in-data-lake-relational-engine-a52d1d9.md "String functions perform conversion, extraction, or manipulation operations on strings, or return information about strings.")

[Function Support of Large Object Data](https://help.sap.com/viewer/a8937bea84f21015a80bc776cf758d50/2023_1_QRC/en-US/a60363a384f21015a7f7bc6286516522.html "Learn about the functions that support the LONG BINARY and LONG VARCHAR data types.") :arrow_upper_right:

[CHAR_LENGTH Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/c440e3a7627544838259dcfab11a5bd1.html "Returns the number of characters in a string.") :arrow_upper_right:

