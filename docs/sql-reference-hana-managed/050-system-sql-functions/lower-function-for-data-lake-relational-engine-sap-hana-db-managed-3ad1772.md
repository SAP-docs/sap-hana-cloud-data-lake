<!-- loio3ad17721e94b4a24a12a07986c829123 -->

# LOWER Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Converts all characters in a string to lowercase.



```
LOWER ( <string-expression> );
```



<a name="loio3ad17721e94b4a24a12a07986c829123__section_z3w_cwg_trb"/>

## Parameters


<dl>
<dt><b>

*<string-expression\>*

</b></dt>
<dd>

The string to be converted.



</dd>
</dl>



<a name="loio3ad17721e94b4a24a12a07986c829123__section_hlk_dwg_trb"/>

## Result Set

-   CHAR
-   NCHAR
-   LONG VARCHAR
-   VARCHAR
-   NVARCHAR



<a name="loio3ad17721e94b4a24a12a07986c829123__section_cxj_jwg_trb"/>

## Remarks

The result data type is a LONG VARCHAR. If you use LOWER in a SELECT INTO statement, you need to use CAST and set LOWER to the correct data type and size.



`LOWER`



<a name="loio3ad17721e94b4a24a12a07986c829123__section_q5b_hwg_trb"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant



<a name="loio3ad17721e94b4a24a12a07986c829123__section_cpt_kwg_trb"/>

## Examples

The following statement returns the value "lower case":

```
SELECT LOWER( 'LOWER CasE' ) FROM iq_dummy;
```

**Related Information**  


[LOWER Function \[String\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a561324784f2101582439eaf6377b80b.html "Converts all characters in a string to lowercase.") :arrow_upper_right:

