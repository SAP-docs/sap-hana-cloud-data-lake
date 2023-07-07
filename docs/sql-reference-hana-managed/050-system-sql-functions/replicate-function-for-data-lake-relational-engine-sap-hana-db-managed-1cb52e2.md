<!-- loio1cb52e270b6c4ce4bc6ed9a00e09af0f -->

# REPLICATE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Concatenates a string a specified number of times.



```
REPLICATE ( <string-expression>, <integer-expression> )
```



<a name="loio1cb52e270b6c4ce4bc6ed9a00e09af0f__section_lmm_5n3_wrb"/>

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



<a name="loio1cb52e270b6c4ce4bc6ed9a00e09af0f__section_lwn_5c5_vrb"/>

## Returns

-   LONG VARCHAR
-   LONG NVARCHAR



<a name="loio1cb52e270b6c4ce4bc6ed9a00e09af0f__section_rqg_vc5_vrb"/>

## Remarks

`REPLICATE` is the same as the `REPEAT` function.

> ### Note:  
> The result data type is a `LONG VARCHAR`. If you use `REPLICATE` in a `SELECT INTO` statement, you must use `CAST` and set `REPLICATE` to the correct data type and size.



<a name="loio1cb52e270b6c4ce4bc6ed9a00e09af0f__section_q3t_vc5_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – compatible with SAP Adaptive Server Enterprise



<a name="loio1cb52e270b6c4ce4bc6ed9a00e09af0f__section_cfj_wc5_vrb"/>

## Example

The following statement returns the value "repeatrepeatrepeat":

```
SELECT REPLICATE( 'repeat', 3 ) FROM iq_dummy
```

**Related Information**  


[REPLICATE Function [String] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a57a156384f2101597df9d785635d3b0.html "Concatenates a string a specified number of times.") :arrow_upper_right:

