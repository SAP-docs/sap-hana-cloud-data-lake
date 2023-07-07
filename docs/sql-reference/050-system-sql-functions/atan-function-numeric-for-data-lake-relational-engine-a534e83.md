<!-- loioa534e83384f21015a17bd5947c1575b2 -->

# ATAN Function \[Numeric\] for Data Lake Relational Engine

Returns the arc-tangent, in radians, of a number.



```
ATAN ( <numeric-expression> )
```



<a name="loioa534e83384f21015a17bd5947c1575b2__ATAN_parm1"/>

## Parameters


<dl>
<dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

The tangent of the angle.



</dd>
</dl>



<a name="loioa534e83384f21015a17bd5947c1575b2__ATAN_returns1"/>

## Returns

DOUBLE



<a name="loioa534e83384f21015a17bd5947c1575b2__ATAN_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa534e83384f21015a17bd5947c1575b2__ATAN_example1"/>

## Example

The following statement returns the value 0.479519:

```
SELECT ATAN( 0.52 ) FROM iq_dummy
```

**Related Information**  


[Trigonometry Functions in Data Lake Relational Engine](trigonometry-functions-in-data-lake-relational-engine-caafd14.md "Some numeric functions return trigonometric information.")

[ATAN Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/4d0428abd20f49fea3612d88cf749e7d.html "Returns the arc-tangent, in radians, of a number.") :arrow_upper_right:

