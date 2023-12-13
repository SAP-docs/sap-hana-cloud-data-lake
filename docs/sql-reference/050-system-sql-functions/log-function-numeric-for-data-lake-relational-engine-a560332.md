<!-- loioa560332084f21015bf3b92161333e171 -->

# LOG Function \[Numeric\] for Data Lake Relational Engine

Returns the natural logarithm of a number.



```
LOG ( <numeric-expression> );
```



<a name="loioa560332084f21015bf3b92161333e171__LOG_parm1"/>

## Parameters


<dl>
<dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

The number.



</dd>
</dl>



<a name="loioa560332084f21015bf3b92161333e171__LOG_returns1"/>

## Result Set

This function converts its argument to DOUBLE, performs the computation in double-precision floating point, and returns a DOUBLE as the result. If the parameter is NULL, the result is NULL.



<a name="loioa560332084f21015bf3b92161333e171__LOG_remarks1"/>

## Remarks

`LN` is an alias of `LOG`.



<a name="loioa560332084f21015bf3b92161333e171__LOG_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa560332084f21015bf3b92161333e171__LOG_examples1"/>

## Example

The following statement returns the value 3.912023:

```
SELECT LOG( 50 ) FROM iq_dummy;
```

**Related Information**  


[LN Function \[Numeric\] for Data Lake Relational Engine](ln-function-numeric-for-data-lake-relational-engine-a55f245.md "Returns the natural logarithm of the specified expression.")

[LOG10 Function \[Numeric\] for Data Lake Relational Engine](log10-function-numeric-for-data-lake-relational-engine-a560b1f.md "Returns the base 10 logarithm of a number.")

[LOG Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/4bedccf5149e42c2bdb12854c1587418.html "Returns the natural logarithm of a number.") :arrow_upper_right:

