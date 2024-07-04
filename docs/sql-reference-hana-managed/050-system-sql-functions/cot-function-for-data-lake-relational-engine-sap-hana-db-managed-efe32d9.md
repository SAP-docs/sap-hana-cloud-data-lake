<!-- loioefe32d94c2374ba4a64f6cac2dfe2cbc -->

# COT Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the cotangent of a number, expressed in radians.



```
COT ( <numeric-expression> );
```



<a name="loioefe32d94c2374ba4a64f6cac2dfe2cbc__section_lv4_qpl_srb"/>

## Parameters


<dl>
<dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

The angle, in radians.



</dd>
</dl>



<a name="loioefe32d94c2374ba4a64f6cac2dfe2cbc__section_mhd_rpl_srb"/>

## Result Set

This function converts its argument to DOUBLE, performs the computation in double-precision floating point, and returns a DOUBLE as the result. If the parameter is NULL, the result is NULL.



<a name="loioefe32d94c2374ba4a64f6cac2dfe2cbc__section_o1t_rpl_srb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioefe32d94c2374ba4a64f6cac2dfe2cbc__section_b5f_spl_srb"/>

## Examples

The following statement returns the value 1.74653:

```
SELECT COT( 0.52 ) FROM iq_dummy;
```

**Related Information**  


[COT Function \[Numeric\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a540f97a84f21015bfc68a88c0565f03.html "Returns the cotangent of a number, expressed in radians.") :arrow_upper_right:

