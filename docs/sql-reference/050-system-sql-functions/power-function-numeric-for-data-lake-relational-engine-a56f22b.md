<!-- loioa56f22b284f210159c928a9db0c5907e -->

# POWER Function \[Numeric\] for Data Lake Relational Engine

Calculates one number raised to the power of another.



```
POWER ( <numeric-expression1>, <numeric-expression2> );
```



<a name="loioa56f22b284f210159c928a9db0c5907e__POWER_parm1"/>

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



<a name="loioa56f22b284f210159c928a9db0c5907e__POWER_returns1"/>

## Result Set

DOUBLE



<a name="loioa56f22b284f210159c928a9db0c5907e__POWER_remarks1"/>

## Remarks

Raises *<numeric-expression1\>* to the power *<numeric-expresson2\>*.



<a name="loioa56f22b284f210159c928a9db0c5907e__POWER_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa56f22b284f210159c928a9db0c5907e__POWER_example1"/>

## Examples

The following statement returns the value 64:

```
SELECT Power( 2, 6 ) FROM iq_dummy;
```

**Related Information**  


[POWER Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/2e3ccb0baaf948029be3400b9c368722.html "Calculates one number raised to the power of another.") :arrow_upper_right:

