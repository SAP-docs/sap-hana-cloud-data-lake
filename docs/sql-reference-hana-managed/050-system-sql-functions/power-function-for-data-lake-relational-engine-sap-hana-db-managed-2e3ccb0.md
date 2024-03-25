<!-- loio2e3ccb0baaf948029be3400b9c368722 -->

# POWER Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Calculates one number raised to the power of another.



```
POWER ( <numeric-expression1>, <numeric-expression2> );
```



<a name="loio2e3ccb0baaf948029be3400b9c368722__section_djq_2pn_vrb"/>

## Parameters


<dl>
<dt><b>

*<numeric-expression1\>*

</b></dt>
<dd>

The base.



</dd><dt><b>

*<numeric-expression2\>*

</b></dt>
<dd>

The exponent.



</dd>
</dl>



<a name="loio2e3ccb0baaf948029be3400b9c368722__section_j4s_fpn_vrb"/>

## Result Set

DOUBLE



<a name="loio2e3ccb0baaf948029be3400b9c368722__section_mpc_gpn_vrb"/>

## Remarks

Raises *<numeric-expression1\>* to the power *<numeric-expresson2\>*.



<a name="loio2e3ccb0baaf948029be3400b9c368722__section_qnr_gpn_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loio2e3ccb0baaf948029be3400b9c368722__section_sds_hpn_vrb"/>

## Example

The following statement returns the value 64:

```
SELECT Power( 2, 6 ) FROM iq_dummy;
```

**Related Information**  


[POWER Function \[Numeric\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a56f22b284f210159c928a9db0c5907e.html "Calculates one number raised to the power of another.") :arrow_upper_right:

