<!-- loio56b6d539c61b44a3a392d9b8f5ba937c -->

# LOG10 Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the base 10 logarithm of a number.



```
LOG10 ( <numeric-expression> );
```



<a name="loio56b6d539c61b44a3a392d9b8f5ba937c__section_qhp_5wg_trb"/>

## Parameters


<dl>
<dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

The number.



</dd>
</dl>



<a name="loio56b6d539c61b44a3a392d9b8f5ba937c__section_hn1_vwg_trb"/>

## Result Set

This function converts its argument to DOUBLE, and performs the computation in double-precision floating point. If the parameter is NULL, the result is NULL.



<a name="loio56b6d539c61b44a3a392d9b8f5ba937c__section_vcr_mgj_wrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loio56b6d539c61b44a3a392d9b8f5ba937c__section_q2d_wwg_trb"/>

## Example

The following statement returns the value 1.698970:

```
SELECT LOG10( 50 ) FROM iq_dummy;
```

**Related Information**  


[LOG10 Function \[Numeric\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a560b1f984f210158a13cb8a24202e26.html "Returns the base 10 logarithm of a number.") :arrow_upper_right:

