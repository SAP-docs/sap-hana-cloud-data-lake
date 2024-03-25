<!-- loiod968d3bd4e5c4662962a776072f95601 -->

# LCASE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Converts all characters in a string to lowercase.



```
LCASE ( <string-expression> );
```



<a name="loiod968d3bd4e5c4662962a776072f95601__section_fbv_vdh_trb"/>

## Parameters


<dl>
<dt><b>

*<string-expression\>*

</b></dt>
<dd>

The string to be converted to lowercase.



</dd>
</dl>



<a name="loiod968d3bd4e5c4662962a776072f95601__section_ivg_wdh_trb"/>

## Result Set

-   CHAR
-   NCHAR
-   LONG VARCHAR
-   VARCHAR
-   NVARCHAR



<a name="loiod968d3bd4e5c4662962a776072f95601__section_lh5_wdh_trb"/>

## Remarks

The result data type is a LONG VARCHAR. If you use LCASE in a SELECT INTO statement, you need to use CAST and set LCASE to the correct data type and size.



<a name="loiod968d3bd4e5c4662962a776072f95601__section_f4n_xdh_trb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loiod968d3bd4e5c4662962a776072f95601__section_rfl_ydh_trb"/>

## Example

The following statement returns the value "lower case":

```
SELECT LCASE( 'LOWER CasE' ) FROM iq_dummy;
```

**Related Information**  


[LCASE Function \[String\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a55c82d484f210158fe3bfeba4f0e0bd.html "Converts all characters in a string to lowercase.") :arrow_upper_right:

