<!-- loio0713b652c6864115aa6b767dbf8531a3 -->

# COS Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the cosine of a number, expressed in radians.



```
COS ( <numeric-expression> )
```



<a name="loio0713b652c6864115aa6b767dbf8531a3__section_rny_cql_srb"/>

## Parameters


<dl>
<dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

The angle, in radians.



</dd>
</dl>



<a name="loio0713b652c6864115aa6b767dbf8531a3__section_wrl_dql_srb"/>

## Returns

This function converts its argument to DOUBLE, performs the computation in double-precision floating point, and returns a DOUBLE as the result. If the parameter is NULL, the result is NULL.



<a name="loio0713b652c6864115aa6b767dbf8531a3__section_w4f_2ql_srb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loio0713b652c6864115aa6b767dbf8531a3__section_z5r_2ql_srb"/>

## Example

The following statement returns the value 0.86781:

```
SELECT COS( 0.52 ) FROM iq_dummy
```

**Related Information**  


[COS Function [Numeric] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a5406e3184f21015956e83d802a05631.html "Returns the cosine of a number, expressed in radians.") :arrow_upper_right:

