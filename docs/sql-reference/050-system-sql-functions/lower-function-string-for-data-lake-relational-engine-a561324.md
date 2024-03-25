<!-- loioa561324784f2101582439eaf6377b80b -->

# LOWER Function \[String\] for Data Lake Relational Engine

Converts all characters in a string to lowercase.



```
LOWER ( <string-expression> );
```



<a name="loioa561324784f2101582439eaf6377b80b__LOWER_parm1"/>

## Parameters


<dl>
<dt><b>

*<string-expression\>*

</b></dt>
<dd>

The string to be converted.



</dd>
</dl>



<a name="loioa561324784f2101582439eaf6377b80b__LOWER_returns1"/>

## Result Set

-   CHAR
-   NCHAR
-   LONG VARCHAR
-   VARCHAR
-   NVARCHAR



<a name="loioa561324784f2101582439eaf6377b80b__LOWER_remarks1"/>

## Remarks

The result data type is a LONG VARCHAR. If you use LOWER in a SELECT INTO statement, you need to use CAST and set LOWER to the correct data type and size.



<a name="loioa561324784f2101582439eaf6377b80b__LOWER_standards1"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant



<a name="loioa561324784f2101582439eaf6377b80b__LOWER_example1"/>

## Example

The following statement returns the value "lower case":

```
SELECT LOWER( 'LOWER CasE' ) FROM iq_dummy;
```

**Related Information**  


[LCASE Function \[String\] for Data Lake Relational Engine](lcase-function-string-for-data-lake-relational-engine-a55c82d.md "Converts all characters in a string to lowercase.")

[LEFT Function \[String\] for Data Lake Relational Engine](left-function-string-for-data-lake-relational-engine-a55d883.md "Returns a specified number of characters from the beginning of a string.")

[REPLACE Function \[String\] for Data Lake Relational Engine](replace-function-string-for-data-lake-relational-engine-a579952.md "Replaces all occurrences of a substring with another substring.")

[REVERSE Function \[String\] for Data Lake Relational Engine](reverse-function-string-for-data-lake-relational-engine-a57a972.md "Takes one argument as an input of type BINARY or STRING and returns the specified string with characters listed in reverse order.")

[RIGHT Function \[String\] for Data Lake Relational Engine](right-function-string-for-data-lake-relational-engine-a57b364.md "Returns the rightmost characters of a string.")

[UCASE Function \[String\] for Data Lake Relational Engine](ucase-function-string-for-data-lake-relational-engine-a58c382.md "Converts all characters in a string to uppercase.")

[UPPER Function \[String\] for Data Lake Relational Engine](upper-function-string-for-data-lake-relational-engine-a58cbc0.md "Converts all characters in a string to uppercase.")

[LOWER Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/3ad17721e94b4a24a12a07986c829123.html "Converts all characters in a string to lowercase.") :arrow_upper_right:

