<!-- loioa57fd70a84f21015a70cd54791443340 -->

# SIN Function \[Numeric\] for Data Lake Relational Engine

Returns the sine of a number, expressed in radians.



```
SIN ( <numeric-expression> )
```



<a name="loioa57fd70a84f21015a70cd54791443340__SIN_parm1"/>

## Parameters


<dl>
<dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

The angle, in radians.



</dd>
</dl>



<a name="loioa57fd70a84f21015a70cd54791443340__SIN_returns1"/>

## Returns

DOUBLE



<a name="loioa57fd70a84f21015a70cd54791443340__SIN_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa57fd70a84f21015a70cd54791443340__SIN_example1"/>

## Example

The following statement returns the value 0.496880:

```
SELECT SIN( 0.52 ) FROM iq_dummy
```

**Related Information**  


[Trigonometry Functions in Data Lake Relational Engine](trigonometry-functions-in-data-lake-relational-engine-caafd14.md "Some numeric functions return trigonometric information.")

[SIN Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/41f4aed677bc4981bfab2a667390fe1a.html "Returns the sine of a number, expressed in radians.") :arrow_upper_right:

