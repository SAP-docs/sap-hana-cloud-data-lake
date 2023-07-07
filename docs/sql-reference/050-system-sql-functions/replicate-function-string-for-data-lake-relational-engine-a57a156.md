<!-- loioa57a156384f2101597df9d785635d3b0 -->

# REPLICATE Function \[String\] for Data Lake Relational Engine

Concatenates a string a specified number of times.



```
REPLICATE ( <string-expression>, <integer-expression> )
```



<a name="loioa57a156384f2101597df9d785635d3b0__REPLICATE_parm1"/>

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

The number of times the string is to be repeated.



</dd>
</dl>



<a name="loioa57a156384f2101597df9d785635d3b0__REPLICATE_returns1"/>

## Returns

-   LONG VARCHAR
-   LONG NVARCHAR



<a name="loioa57a156384f2101597df9d785635d3b0__REPLICATE_remarks1"/>

## Remarks

`REPLICATE` is the same as the `REPEAT` function.

> ### Note:  
> The result data type is a `LONG VARCHAR`. If you use `REPLICATE` in a `SELECT INTO` statement, you must use `CAST` and set `REPLICATE` to the correct data type and size.



<a name="loioa57a156384f2101597df9d785635d3b0__REPLICATE_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – compatible with SAP Adaptive Server Enterprise



<a name="loioa57a156384f2101597df9d785635d3b0__REPLICATE_example1"/>

## Example

The following statement returns the value "repeatrepeatrepeat":

```
SELECT REPLICATE( 'repeat', 3 ) FROM iq_dummy
```

**Related Information**  


[REPEAT Function \[String\] for Data Lake Relational Engine](repeat-function-string-for-data-lake-relational-engine-a579104.md "Concatenates a string a specified number of times.")

[REPLACE Function \[String\] for Data Lake Relational Engine](replace-function-string-for-data-lake-relational-engine-a579952.md "Replaces all occurrences of a substring with another substring.")

[REPLICATE Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/1cb52e270b6c4ce4bc6ed9a00e09af0f.html "Concatenates a string a specified number of times.") :arrow_upper_right:

