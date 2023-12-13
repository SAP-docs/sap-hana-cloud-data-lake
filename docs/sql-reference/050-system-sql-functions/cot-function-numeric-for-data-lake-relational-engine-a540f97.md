<!-- loioa540f97a84f21015bfc68a88c0565f03 -->

# COT Function \[Numeric\] for Data Lake Relational Engine

Returns the cotangent of a number, expressed in radians.



```
COT ( <numeric-expression> );
```



<a name="loioa540f97a84f21015bfc68a88c0565f03__COT_parm1"/>

## Parameters


<dl>
<dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

The angle, in radians.



</dd>
</dl>



<a name="loioa540f97a84f21015bfc68a88c0565f03__COT_returns1"/>

## Result Set

This function converts its argument to DOUBLE, performs the computation in double-precision floating point, and returns a DOUBLE as the result. If the parameter is NULL, the result is NULL.



<a name="loioa540f97a84f21015bfc68a88c0565f03__COT_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa540f97a84f21015bfc68a88c0565f03__COT_example1"/>

## Example

The following statement returns the value 1.74653:

```
SELECT COT( 0.52 ) FROM iq_dummy;
```

**Related Information**  


[Trigonometry Functions in Data Lake Relational Engine](trigonometry-functions-in-data-lake-relational-engine-caafd14.md "Some numeric functions return trigonometric information.")

[COT Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/efe32d94c2374ba4a64f6cac2dfe2cbc.html "Returns the cotangent of a number, expressed in radians.") :arrow_upper_right:

