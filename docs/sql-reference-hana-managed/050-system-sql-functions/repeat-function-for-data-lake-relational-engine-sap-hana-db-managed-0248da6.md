<!-- loio0248da66d3bf4d7ba425f5b4f20ba6cc -->

# REPEAT Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Concatenates a string a specified number of times.



```
REPEAT ( <string-expression>, <integer-expression> )
```



<a name="loio0248da66d3bf4d7ba425f5b4f20ba6cc__section_g32_l25_vrb"/>

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



<a name="loio0248da66d3bf4d7ba425f5b4f20ba6cc__section_mxp_nn3_wrb"/>

## Returns

-   LONG VARCHAR
-   LONG NVARCHAR



<a name="loio0248da66d3bf4d7ba425f5b4f20ba6cc__section_fqs_4n3_wrb"/>

## Remarks

> ### Note:  
> The result data type is a `LONG VARCHAR`. If you use `REPEAT` in a `SELECT INTO` statement, you must use `CAST` and set REPEAT to the correct data type and size.



<a name="loio0248da66d3bf4d7ba425f5b4f20ba6cc__section_jzj_pn3_wrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar.
-   SAP database products – not supported by SAP Adaptive Server Enterprise, but `REPLICATE` provides the same capabilities.



<a name="loio0248da66d3bf4d7ba425f5b4f20ba6cc__section_nxg_n25_vrb"/>

## Example

The following statement returns the value "repeatrepeatrepeat":

```
SELECT REPEAT( 'repeat', 3 ) FROM iq_dummy
```

**Related Information**  


[REPEAT Function [String] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a579104184f2101598d4cd02edf61346.html "Concatenates a string a specified number of times.") :arrow_upper_right:

