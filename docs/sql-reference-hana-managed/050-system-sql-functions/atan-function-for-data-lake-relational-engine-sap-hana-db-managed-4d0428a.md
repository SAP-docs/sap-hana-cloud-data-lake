<!-- loio4d0428abd20f49fea3612d88cf749e7d -->

# ATAN Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the arc-tangent, in radians, of a number.



```
ATAN ( <numeric-expression> );
```



<a name="loio4d0428abd20f49fea3612d88cf749e7d__section_sqc_x3k_srb"/>

## Parameters


<dl>
<dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

The tangent of the angle.



</dd>
</dl>



<a name="loio4d0428abd20f49fea3612d88cf749e7d__section_bbp_x3k_srb"/>

## Result Set

DOUBLE



<a name="loio4d0428abd20f49fea3612d88cf749e7d__section_qr1_y3k_srb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loio4d0428abd20f49fea3612d88cf749e7d__section_gpn_y3k_srb"/>

## Example

The following statement returns the value 0.479519:

```
SELECT ATAN( 0.52 ) FROM iq_dummy;
```

**Related Information**  


[ATAN Function \[Numeric\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a534e83384f21015a17bd5947c1575b2.html "Returns the arc-tangent, in radians, of a number.") :arrow_upper_right:

