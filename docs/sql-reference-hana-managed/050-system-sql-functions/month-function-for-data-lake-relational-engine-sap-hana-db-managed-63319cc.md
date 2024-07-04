<!-- loio63319ccc3d6847fab168f3418d0fec07 -->

# MONTH Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns a number from 1 to 12 corresponding to the month of the given date.



```
MONTH ( <date-expression> );
```



<a name="loio63319ccc3d6847fab168f3418d0fec07__section_nnk_3fn_vrb"/>

## Parameters


<dl>
<dt><b>

*<date-expression\>*

</b></dt>
<dd>

A date/time value.



</dd>
</dl>



<a name="loio63319ccc3d6847fab168f3418d0fec07__section_j1h_jfn_vrb"/>

## Result Set

SMALLINT



<a name="loio63319ccc3d6847fab168f3418d0fec07__section_hhr_jfn_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loio63319ccc3d6847fab168f3418d0fec07__section_qg3_kfn_vrb"/>

## Examples

The following statement returns the value 7:

```
SELECT MONTH( '1998-07-13' ) FROM iq_dummy;
```

**Related Information**  


[MONTH Function \[Date and Time\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a565928184f21015aecd84c01c4c2078.html "Returns a number from 1 to 12 corresponding to the month of the given date.") :arrow_upper_right:

