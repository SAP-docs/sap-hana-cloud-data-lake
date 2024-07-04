<!-- loio4bedccf5149e42c2bdb12854c1587418 -->

# LOG Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the natural logarithm of a number.



```
LOG ( <numeric-expression> );
```



<a name="loio4bedccf5149e42c2bdb12854c1587418__section_kwq_1yg_trb"/>

## Parameters


<dl>
<dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

The number.



</dd>
</dl>



<a name="loio4bedccf5149e42c2bdb12854c1587418__section_zvf_byg_trb"/>

## Result Set

This function converts its argument to DOUBLE, performs the computation in double-precision floating point, and returns a DOUBLE as the result. If the parameter is NULL, the result is NULL.



<a name="loio4bedccf5149e42c2bdb12854c1587418__section_nbs_byg_trb"/>

## Remarks

`LN` is an alias of `LOG`.



<a name="loio4bedccf5149e42c2bdb12854c1587418__section_a1d_cyg_trb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loio4bedccf5149e42c2bdb12854c1587418__section_hpt_cyg_trb"/>

## Examples

The following statement returns the value 3.912023:

```
SELECT LOG( 50 ) FROM iq_dummy;
```

**Related Information**  


[LOG Function \[Numeric\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a560332084f21015bf3b92161333e171.html "Returns the natural logarithm of a number.") :arrow_upper_right:

