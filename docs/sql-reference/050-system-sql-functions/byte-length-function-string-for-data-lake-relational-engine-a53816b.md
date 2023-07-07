<!-- loioa53816b784f210159b849878d71ab1a8 -->

# BYTE\_LENGTH Function \[String\] for Data Lake Relational Engine

Returns the number of bytes in a string.



```
BYTE_LENGTH ( <string-expression> )
```



<a name="loioa53816b784f210159b849878d71ab1a8__BYTE_LENGTH_parm1"/>

## Parameters


<dl>
<dt><b>

*<string-expression\>*

</b></dt>
<dd>

The string that has the length to be calculated.



</dd>
</dl>



<a name="loioa53816b784f210159b849878d71ab1a8__BYTE_LENGTH_returns1"/>

## Returns

INT



<a name="loioa53816b784f210159b849878d71ab1a8__BYTE_LENGTH_remarks1"/>

## Remarks

Trailing white space characters are included in the length returned.

The return value of a NULL string is NULL.

If the string is in a multibyte character set, the `BYTE_LENGTH` value differs from the number of characters returned by `CHAR_LENGTH`.

The `BYTE_LENGTH` function supports both `LONG BINARY` columns and variables and `LONG VARCHAR` columns and variables, only if the query returns less than 2 GB. If the byte length of the returned `LONG BINARY` or `LONG VARCHAR` data is greater than or equal to 2 GB, `BYTE_LENGTH` returns an error that says you must use the `BYTE_LENGTH64` function.



<a name="loioa53816b784f210159b849878d71ab1a8__BYTE_LENGTH_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa53816b784f210159b849878d71ab1a8__BYTE_LENGTH_example1"/>

## Example

Returns the value 12:

```
SELECT BYTE_LENGTH( 'Test Message' ) FROM iq_dummy
```

**Related Information**  


[String Functions in Data Lake Relational Engine](string-functions-in-data-lake-relational-engine-a52d1d9.md "String functions perform conversion, extraction, or manipulation operations on strings, or return information about strings.")

[Function Support of Large Object Data](https://help.sap.com/viewer/a8937bea84f21015a80bc776cf758d50/2023_2_QRC/en-US/a60363a384f21015a7f7bc6286516522.html "Learn about the functions that support the LONG BINARY and LONG VARCHAR data types.") :arrow_upper_right:

[BYTE_LENGTH Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/da0bd303497b4828b0c89f22e692a6c5.html "Returns the number of bytes in a string.") :arrow_upper_right:

