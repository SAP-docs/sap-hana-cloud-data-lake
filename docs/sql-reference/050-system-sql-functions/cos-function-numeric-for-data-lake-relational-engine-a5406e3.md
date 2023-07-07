<!-- loioa5406e3184f21015956e83d802a05631 -->

# COS Function \[Numeric\] for Data Lake Relational Engine

Returns the cosine of a number, expressed in radians.



```
COS ( <numeric-expression> )
```



<a name="loioa5406e3184f21015956e83d802a05631__COS_parm1"/>

## Parameters


<dl>
<dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

The angle, in radians.



</dd>
</dl>



<a name="loioa5406e3184f21015956e83d802a05631__COS_returns1"/>

## Returns

This function converts its argument to DOUBLE, performs the computation in double-precision floating point, and returns a DOUBLE as the result. If the parameter is NULL, the result is NULL.



<a name="loioa5406e3184f21015956e83d802a05631__COS_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa5406e3184f21015956e83d802a05631__COS_example1"/>

## Example

The following statement returns the value 0.86781:

```
SELECT COS( 0.52 ) FROM iq_dummy
```

**Related Information**  


[Trigonometry Functions in Data Lake Relational Engine](trigonometry-functions-in-data-lake-relational-engine-caafd14.md "Some numeric functions return trigonometric information.")

[COS Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/0713b652c6864115aa6b767dbf8531a3.html "Returns the cosine of a number, expressed in radians.") :arrow_upper_right:

