<!-- loioa579104184f2101598d4cd02edf61346 -->

# REPEAT Function \[String\] for Data Lake Relational Engine

Concatenates a string a specified number of times.



```
REPEAT ( <string-expression>, <integer-expression> );
```



<a name="loioa579104184f2101598d4cd02edf61346__REPEAT_parm1"/>

## Parameters


<dl>
<dt><b>

*<string-expression\>*

</b></dt>
<dd>

The string to be repeated.



</dd><dt><b>

*<integer-expression\>*

</b></dt>
<dd>

The number of times the string is to be repeated. If *<integer-expression\>* is negative, an empty string is returned.



</dd>
</dl>



<a name="loioa579104184f2101598d4cd02edf61346__REPEAT_returs1"/>

## Result Set

-   LONG VARCHAR
-   LONG NVARCHAR



<a name="loioa579104184f2101598d4cd02edf61346__REPEAT_remarks1"/>

## Remarks

> ### Note:  
> The result data type is a `LONG VARCHAR`. If you use `REPEAT` in a `SELECT INTO` statement, you must use `CAST` and set REPEAT to the correct data type and size.



<a name="loioa579104184f2101598d4cd02edf61346__REPEAT_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar.
-   SAP database products – not supported by SAP Adaptive Server Enterprise, but `REPLICATE` provides the same capabilities.



<a name="loioa579104184f2101598d4cd02edf61346__REPEAT_Examples1"/>

## Examples

The following statement returns the value "repeatrepeatrepeat":

```
SELECT REPEAT( 'repeat', 3 ) FROM iq_dummy;
```

**Related Information**  


[REPLACE Function \[String\] for Data Lake Relational Engine](replace-function-string-for-data-lake-relational-engine-a579952.md "Replaces all occurrences of a substring with another substring.")

[REPLICATE Function \[String\] for Data Lake Relational Engine](replicate-function-string-for-data-lake-relational-engine-a57a156.md "Concatenates a string a specified number of times.")

[REPEAT Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/0248da66d3bf4d7ba425f5b4f20ba6cc.html "Concatenates a string a specified number of times.") :arrow_upper_right:

