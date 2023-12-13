<!-- loioa58cbc0284f21015ac14f5baa190b878 -->

# UPPER Function \[String\] for Data Lake Relational Engine

Converts all characters in a string to uppercase.



```
UPPER ( <string-expression> );
```



<a name="loioa58cbc0284f21015ac14f5baa190b878__UPPER_parm1"/>

## Parameters


<dl>
<dt><b>

*<string-expression\>*

</b></dt>
<dd>

The string to be converted to uppercase.



</dd>
</dl>



<a name="loioa58cbc0284f21015ac14f5baa190b878__UPPER_returns1"/>

## Result Set

-   LONG NVARCHAR
-   LONG VARCHAR
-   NVARCHAR
-   VARCHAR

> ### Note:  
> The result data type is a `LONG VARCHAR`. If you use `UPPER` in a `SELECT INTO` statement, you must use `CAST` and set `UPPER` to the correct data type and size.



<a name="loioa58cbc0284f21015ac14f5baa190b878__UPPER_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – compatible with SAP Adaptive Server Enterprise



<a name="loioa58cbc0284f21015ac14f5baa190b878__UPPER_example1"/>

## Example

The following statement returns the value “CHOCOLATE”:

```
SELECT UPPER( 'ChocoLate' ) FROM iq_dummy;
```

**Related Information**  


[LCASE Function \[String\] for Data Lake Relational Engine](lcase-function-string-for-data-lake-relational-engine-a55c82d.md "Converts all characters in a string to lowercase.")

[LEFT Function \[String\] for Data Lake Relational Engine](left-function-string-for-data-lake-relational-engine-a55d883.md "Returns a specified number of characters from the beginning of a string.")

[LOWER Function \[String\] for Data Lake Relational Engine](lower-function-string-for-data-lake-relational-engine-a561324.md "Converts all characters in a string to lowercase.")

[REPLACE Function \[String\] for Data Lake Relational Engine](replace-function-string-for-data-lake-relational-engine-a579952.md "Replaces all occurrences of a substring with another substring.")

[REVERSE Function \[String\] for Data Lake Relational Engine](reverse-function-string-for-data-lake-relational-engine-a57a972.md "Takes one argument as an input of type BINARY or STRING and returns the specified string with characters listed in reverse order.")

[RIGHT Function \[String\] for Data Lake Relational Engine](right-function-string-for-data-lake-relational-engine-a57b364.md "Returns the rightmost characters of a string.")

[UCASE Function \[String\] for Data Lake Relational Engine](ucase-function-string-for-data-lake-relational-engine-a58c382.md "Converts all characters in a string to uppercase.")

[UPPER Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/10843333345b407694db50383c73a083.html "Converts all characters in a string to uppercase.") :arrow_upper_right:

