<!-- loioa532c20484f21015a4a5f8c26e3af9c7 -->

# ACOS Function \[Numeric\] for Data Lake Relational Engine

Returns the arc-cosine, in radians, of a numeric expression.



```
ACOS ( <numeric-expression> );
```



<a name="loioa532c20484f21015a4a5f8c26e3af9c7__ACOS_parm1"/>

## Parameters


<dl>
<dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

The cosine of the angle.



</dd>
</dl>



<a name="loioa532c20484f21015a4a5f8c26e3af9c7__ACOS_returns1"/>

## Result Set

DOUBLE



<a name="loioa532c20484f21015a4a5f8c26e3af9c7__ACOS_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa532c20484f21015a4a5f8c26e3af9c7__ACOS_example1"/>

## Examples

The following statement returns the value 1.023945:

```
SELECT ACOS( 0.52 ) FROM iq_dummy;
```

**Related Information**  


[ACOS Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/0fc7b1b85c8d4b6280000fc7e92152ee.html "Returns the arc-cosine, in radians, of a numeric expression.") :arrow_upper_right:

