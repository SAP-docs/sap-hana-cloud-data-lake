<!-- loiobe690a0aa62c4e67986070c70f25b3fe -->

# DAYNAME Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the name of the day of the week from the specified date.



```
DAYNAME ( <date-expression> );
```



<a name="loiobe690a0aa62c4e67986070c70f25b3fe__section_jgh_4bm_srb"/>

## Parameters


<dl>
<dt><b>

*<date-expression\>*

</b></dt>
<dd>

The date.



</dd>
</dl>



<a name="loiobe690a0aa62c4e67986070c70f25b3fe__section_z2w_4bm_srb"/>

## Result Set

VARCHAR



<a name="loiobe690a0aa62c4e67986070c70f25b3fe__section_dsf_pbm_srb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loiobe690a0aa62c4e67986070c70f25b3fe__section_j31_vl3_wrb"/>

## Examples

The following statement returns the value Saturday:

```
SELECT DAYNAME ( '1987/05/02' ) FROM iq_dummy;
```

**Related Information**  


[DAYNAME Function \[Date and Time\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a549c43b84f21015a569d8e52c4af3f8.html "Returns the name of the day of the week from the specified date.") :arrow_upper_right:

