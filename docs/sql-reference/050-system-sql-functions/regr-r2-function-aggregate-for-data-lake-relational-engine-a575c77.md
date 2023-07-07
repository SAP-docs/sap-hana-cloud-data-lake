<!-- loioa575c77684f210158d23e68bbd456148 -->

# REGR\_R2 Function \[Aggregate\] for Data Lake Relational Engine

Computes the coefficient of determination \(also referred to as R-squared or the goodness-of-fit statistic\) for the regression line.




<dl>
<dt><b>

Syntax 1

</b></dt>
<dd>

```
REGR_R2( <dependent-expression>, <independent-expression> )
```



</dd><dt><b>

Syntax 2

</b></dt>
<dd>

```
REGR_R2( <dependent-expression>, <independent-expression> )
OVER ( <window-spec> )
```



</dd>
</dl>



<a name="loioa575c77684f210158d23e68bbd456148__REGR_R2_parm1"/>

## Parameters


<dl>
<dt><b>

*<dependent-expression\>*

</b></dt>
<dd>

The variable that is affected by the independent variable.



</dd><dt><b>

*<independent-expression\>*

</b></dt>
<dd>

The variable that influences the outcome.



</dd><dt><b>

*<window-spec\>*

</b></dt>
<dd>

Specified when using this function as a window function.



</dd>
</dl>



<a name="loioa575c77684f210158d23e68bbd456148__REGR_R2_returns1"/>

## Returns

DOUBLE



<a name="loioa575c77684f210158d23e68bbd456148__REGR_R2_remarks1"/>

## Remarks

This function converts its arguments to DOUBLE, performs the computation in double-precision floating-point, and returns a DOUBLE as the result. If applied to an empty set, then `REGR_R2` returns NULL.

`REGR_R2` is applied to the set of \(*<dependent-expression\>* and *<independent-expression\>*\) pairs after eliminating all pairs for which either *<dependent-expression\>* or *<independent-expression\>* is NULL. Data lake Relational Engine then applies the following algorithm, where *<y\>* represents the *<dependent-expression\>* and *<x\>* represents the *<independent-expression\>*:

-   `REGR_R2` calculates `VAR_POP(x)` and returns NULL if `VAR_POP(x) = 0`; otherwise, it calculates `VAR_POP(y)` and returns the value 1 if `VAR_POP(y) = 0`.
-   If neither `VAR_POP(x)` or `VAR_POP(y)` is zero, the return value is `POWER(CORR(y,x),2)`.

> ### Note:  
> ROLLUP and CUBE are not supported in the `GROUP BY` clause with Syntax 1. `DISTINCT` is not supported.

Syntax 2 – The *<window-spec\>* parameter represents usage as a window function in a `SELECT` statement. As such, you can specify elements of *<window-spec\>* either in the function syntax \(inline\), or with a `WINDOW` clause in the `SELECT` statement.



<a name="loioa575c77684f210158d23e68bbd456148__REGR_R2_standards1"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant. SQL/OLAP feature T612.
-   SAP database products – compatible with SAP SQL Anywhere



<a name="loioa575c77684f210158d23e68bbd456148__REGR_R2_examples1"/>

## Example

The following example returns the value 0.19379959710325653:

```
SELECT REGR_R2( Salary, ( YEAR( NOW() ) - YEAR( BirthDate ) ) )FROM Employees;
```

**Related Information**  


[Windowing Aggregate Function Usage in Data Lake Relational Engine](windowing-aggregate-function-usage-in-data-lake-relational-engine-a527f35.md "A major feature of the ISO/ANSI SQL extensions for OLAP is a construct called a window.")

[REGR_R2 Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/e970c79f12d44021b872f41c9f5ce7d9.html "Computes the coefficient of determination (also referred to as R-squared or the goodness-of-fit statistic) for the regression line.") :arrow_upper_right:

