<!-- loioa534668f84f2101599958685dfc4673b -->

# ASIN Function \[Numeric\] for Data Lake Relational Engine

Returns the arc-sine, in radians, of a number.



```
ASIN ( <numeric-expression> );
```



<a name="loioa534668f84f2101599958685dfc4673b__ASIN_parm1"/>

## Parameters


<dl>
<dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

The sine of the angle.



</dd>
</dl>



<a name="loioa534668f84f2101599958685dfc4673b__ASIN_returns1"/>

## Result Set

DOUBLE



<a name="loioa534668f84f2101599958685dfc4673b__ASIN_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa534668f84f2101599958685dfc4673b__ASIN_example1"/>

## Examples

The following statement returns the value 0.546850:

```
SELECT ASIN( 0.52 ) FROM iq_dummy;
```

**Related Information**  


[Trigonometry Functions in Data Lake Relational Engine](trigonometry-functions-in-data-lake-relational-engine-caafd14.md "Some numeric functions return trigonometric information.")

[ASIN Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/a56e5e54ba234675b4a5c30b13e933e9.html "Returns the arc-sine, in radians, of a number.") :arrow_upper_right:

