<!-- loiodbeab0046dff49e89f016a8496e978f8 -->

# RADIANS Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Converts a number from degrees to radians.



```
RADIANS ( <numeric-expression> )
```



<a name="loiodbeab0046dff49e89f016a8496e978f8__section_srz_xm5_vrb"/>

## Parameters


<dl>
<dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

A number, in degrees. This angle is converted to radians



</dd>
</dl>



<a name="loiodbeab0046dff49e89f016a8496e978f8__section_lvz_zm5_vrb"/>

## Returns

DOUBLE



<a name="loiodbeab0046dff49e89f016a8496e978f8__section_eyj_1n5_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loiodbeab0046dff49e89f016a8496e978f8__section_hkz_1n5_vrb"/>

## Example

The following statement returns a value of approximately 0.5236:

```
SELECT RADIANS( 30 ) FROM iq_dummy
```

**Related Information**  


[RADIANS Function [Numeric] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a572340384f21015b1d3dab0d7a76062.html "Converts a number from degrees to radians.") :arrow_upper_right:

