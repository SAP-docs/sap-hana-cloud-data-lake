<!-- loioa56e5e54ba234675b4a5c30b13e933e9 -->

# ASIN Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the arc-sine, in radians, of a number.



```
ASIN ( <numeric-expression> );
```



<a name="loioa56e5e54ba234675b4a5c30b13e933e9__section_mn3_hjk_srb"/>

## Parameters


<dl>
<dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

The sine of the angle.



</dd>
</dl>



<a name="loioa56e5e54ba234675b4a5c30b13e933e9__section_ovt_hjk_srb"/>

## Result Set

DOUBLE



<a name="loioa56e5e54ba234675b4a5c30b13e933e9__section_r2h_3jk_srb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa56e5e54ba234675b4a5c30b13e933e9__section_lfc_jjk_srb"/>

## Example

The following statement returns the value 0.546850:

```
SELECT ASIN( 0.52 ) FROM iq_dummy;
```

**Related Information**  


[ASIN Function \[Numeric\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a534668f84f2101599958685dfc4673b.html "Returns the arc-sine, in radians, of a number.") :arrow_upper_right:

