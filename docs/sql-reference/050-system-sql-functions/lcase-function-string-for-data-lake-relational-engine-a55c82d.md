<!-- loioa55c82d484f210158fe3bfeba4f0e0bd -->

# LCASE Function \[String\] for Data Lake Relational Engine

Converts all characters in a string to lowercase.



```
LCASE ( <string-expression> )
```



<a name="loioa55c82d484f210158fe3bfeba4f0e0bd__LCASE_parm1"/>

## Parameters


<dl>
<dt><b>

*<string-expression\>*

</b></dt>
<dd>

The string to be converted to lowercase.



</dd>
</dl>



<a name="loioa55c82d484f210158fe3bfeba4f0e0bd__LCASE_returns1"/>

## Returns

-   CHAR
-   NCHAR
-   LONG VARCHAR
-   VARCHAR
-   NVARCHAR



<a name="loioa55c82d484f210158fe3bfeba4f0e0bd__LCASE_remarks1"/>

## Remarks

The result data type is a LONG VARCHAR. If you use LCASE in a SELECT INTO statement, you need to use CAST and set LCASE to the correct data type and size.



<a name="loioa55c82d484f210158fe3bfeba4f0e0bd__LCASE_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa55c82d484f210158fe3bfeba4f0e0bd__LCASE_example1"/>

## Example

The following statement returns the value "lower case":

```
SELECT LCASE( 'LOWER CasE' ) FROM iq_dummy
```

**Related Information**  


[LEFT Function \[String\] for Data Lake Relational Engine](left-function-string-for-data-lake-relational-engine-a55d883.md "Returns a specified number of characters from the beginning of a string.")

[LOWER Function \[String\] for Data Lake Relational Engine](lower-function-string-for-data-lake-relational-engine-a561324.md "Converts all characters in a string to lowercase.")

[REPLACE Function \[String\] for Data Lake Relational Engine](replace-function-string-for-data-lake-relational-engine-a579952.md "Replaces all occurrences of a substring with another substring.")

[REVERSE Function \[String\] for Data Lake Relational Engine](reverse-function-string-for-data-lake-relational-engine-a57a972.md "Takes one argument as an input of type BINARY or STRING and returns the specified string with characters listed in reverse order.")

[RIGHT Function \[String\] for Data Lake Relational Engine](right-function-string-for-data-lake-relational-engine-a57b364.md "Returns the rightmost characters of a string.")

[UCASE Function \[String\] for Data Lake Relational Engine](ucase-function-string-for-data-lake-relational-engine-a58c382.md "Converts all characters in a string to uppercase.")

[UPPER Function \[String\] for Data Lake Relational Engine](upper-function-string-for-data-lake-relational-engine-a58cbc0.md "Converts all characters in a string to uppercase.")

[LCASE Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/d968d3bd4e5c4662962a776072f95601.html "Converts all characters in a string to lowercase.") :arrow_upper_right:

