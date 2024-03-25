<!-- loioa5356c1b84f210159f68d03274510fe6 -->

# ATAN2 Function \[Numeric\] for Data Lake Relational Engine

Returns the arc-tangent, in radians, of the ratio of two numbers.



```
ATAN2 ( <numeric-expression1>, <numeric-expression2> );
```



<a name="loioa5356c1b84f210159f68d03274510fe6__ATAN2_parm1"/>

## Parameters


<dl>
<dt><b>

*<numeric-expression1\>*

</b></dt>
<dd>

The numerator in the ratio whose arc tangent is calculated.



</dd><dt><b>

*<numeric-expression2\>*

</b></dt>
<dd>

The denominator in the ratio whose arc-tangent is calculated.



</dd>
</dl>



<a name="loioa5356c1b84f210159f68d03274510fe6__ATAN2_returns1"/>

## Result Set

DOUBLE



<a name="loioa5356c1b84f210159f68d03274510fe6__ATAN2_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa5356c1b84f210159f68d03274510fe6__ATAN2_example1"/>

## Example

The following statement returns the value 0.00866644968879073143:

```
SELECT ATAN2( 0.52, 060 ) FROM iq_dummy;
```

**Related Information**  


[Trigonometry Functions in Data Lake Relational Engine](trigonometry-functions-in-data-lake-relational-engine-caafd14.md "Some numeric functions return trigonometric information.")

[ATAN2 Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/8081001d5f8e4323a5f13cc57fb91cf1.html "Returns the arc-tangent, in radians, of the ratio of two numbers.") :arrow_upper_right:

