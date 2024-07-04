<!-- loioa58c382984f2101586a7d1f6dcf499c3 -->

# UCASE Function \[String\] for Data Lake Relational Engine

Converts all characters in a string to uppercase.



```
UCASE ( <string-expression> );
```



<a name="loioa58c382984f2101586a7d1f6dcf499c3__UCASE_parm1"/>

## Parameters


<dl>
<dt><b>

*<string-expression\>*

</b></dt>
<dd>

The string to be converted to uppercase.



</dd>
</dl>



<a name="loioa58c382984f2101586a7d1f6dcf499c3__UCASE_ruturns1"/>

## Result Set

-   LONG NVARCHAR
-   LONG VARCHAR
-   NVARCHAR
-   VARCHAR

> ### Note:  
> The result data type is a `LONG VARCHAR`. If you use `UCASE` in a `SELECT INTO` statement, you must use `CAST` and set `UCASE` to the correct data type and size.



<a name="loioa58c382984f2101586a7d1f6dcf499c3__UCASE_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar.
-   SAP database products – `UCASE` is not supported by SAP Adaptive Server Enterprise, but `UPPER` provides the same feature in a compatible manner.



<a name="loioa58c382984f2101586a7d1f6dcf499c3__UCASE_example1"/>

## Examples

The following statement returns the value “CHOCOLATE”:

```
SELECT UCASE( 'ChocoLate' ) FROM iq_dummy;
```

**Related Information**  


[LCASE Function \[String\] for Data Lake Relational Engine](lcase-function-string-for-data-lake-relational-engine-a55c82d.md "Converts all characters in a string to lowercase.")

[LEFT Function \[String\] for Data Lake Relational Engine](left-function-string-for-data-lake-relational-engine-a55d883.md "Returns a specified number of characters from the beginning of a string.")

[LOWER Function \[String\] for Data Lake Relational Engine](lower-function-string-for-data-lake-relational-engine-a561324.md "Converts all characters in a string to lowercase.")

[REPLACE Function \[String\] for Data Lake Relational Engine](replace-function-string-for-data-lake-relational-engine-a579952.md "Replaces all occurrences of a substring with another substring.")

[REVERSE Function \[String\] for Data Lake Relational Engine](reverse-function-string-for-data-lake-relational-engine-a57a972.md "Takes one argument as an input of type BINARY or STRING and returns the specified string with characters listed in reverse order.")

[RIGHT Function \[String\] for Data Lake Relational Engine](right-function-string-for-data-lake-relational-engine-a57b364.md "Returns the rightmost characters of a string.")

[UPPER Function \[String\] for Data Lake Relational Engine](upper-function-string-for-data-lake-relational-engine-a58cbc0.md "Converts all characters in a string to uppercase.")

[UCASE_syntax Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/3c1a297f45ba489283c80d39e97a4218.html "Converts all characters in a string to uppercase.") :arrow_upper_right:

