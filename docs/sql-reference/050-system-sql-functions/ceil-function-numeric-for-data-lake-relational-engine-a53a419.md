<!-- loioa53a419c84f21015b689e542cbf26996 -->

# CEIL Function \[Numeric\] for Data Lake Relational Engine

Returns the smallest integer greater than or equal to the specified expression.



```
CEIL ( <numeric-expression> );
```



<a name="loioa53a419c84f21015b689e542cbf26996__CEIL_parm1"/>

## Parameters


<dl>
<dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

A column, variable, or expression with a data type that is either exact numeric, approximate numeric, money, or any type that can be implicitly converted to one of these types. For other data types, `CEIL` generates an error. The return value has the same data type as the value supplied.



</dd>
</dl>



<a name="loioa53a419c84f21015b689e542cbf26996__CEIL_remarks1"/>

## Remarks

`CEIL` is as synonym for `CEILING`.

For a given expression, the `CEIL` function takes one argument. For example, `CEIL (-123.45)` returns `-123`. `CEIL (123.45)` returns `124`.



<a name="loioa53a419c84f21015b689e542cbf26996__CEIL_standards1"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant

**Related Information**  


[FLOOR Function \[Numeric\] for Data Lake Relational Engine](floor-function-numeric-for-data-lake-relational-engine-a552c1c.md "Returns the floor of (largest integer not greater than) a number.")

[CEILING Function \[Numeric\] for Data Lake Relational Engine](ceiling-function-numeric-for-data-lake-relational-engine-a53acd1.md "Returns the ceiling (smallest integer not less than) of a number.")

[CEIL Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/cf884aecfedf41a49b65a4082fa91ffa.html "Returns the smallest integer greater than or equal to the specified expression.") :arrow_upper_right:

