<!-- loioa541901c84f21015b699cc40f6738ebc -->

# COVAR\_POP Function \[Aggregate\] for Data Lake Relational Engine

Returns the population covariance of a set of number pairs.




<dl>
<dt><b>

Syntax 1

</b></dt>
<dd>

```
COVAR_POP ( <dependent-expression>, <independent-expression> )
```



</dd><dt><b>

Syntax 2

</b></dt>
<dd>

```
COVAR_POP (<dependent-expression>, <independent-expression> )
OVER ( <window-spec> )
```



</dd>
</dl>



<a name="loioa541901c84f21015b699cc40f6738ebc__COVAR_POP_parm1"/>

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



<a name="loioa541901c84f21015b699cc40f6738ebc__COVAR_POP_remarks1"/>

## Remarks

This function converts its arguments to DOUBLE, performs the computation in double-precision floating-point, and returns a DOUBLE as the result. If applied to an empty set, then `COVAR_POP` returns NULL.

Both *<dependent-expression\>* and *<independent-expression\>* are numeric. The function is applied to the set of \(*<dependent-expression\>*, *<independent-expression\>*\) after eliminating the pairs for which either *<dependent-expression\>* or *<independent-expression\>* is NULL. The following computation is made, where *<x\>* represents *<dependent-expression\>* and *<y\>* represents *<independent-expression\>*:

```
(SUM(x*y) - SUM(x) * SUM(y) / n) / n
```

> ### Note:  
> ROLLUP and CUBE are not supported in the `GROUP BY` clause with Syntax 1. DISTINCT is not supported.

Syntax 2 – The *<window-spec\>* parameter represents usage as a window function in a `SELECT` statement. As such, you can specify elements of *<window-spec\>* either in the function syntax \(inline\), or with a `WINDOW` clause in the `SELECT` statement.



<a name="loioa541901c84f21015b699cc40f6738ebc__COVAR_POP_standards1"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant SQL foundation feature outside of core SQL.



<a name="loioa541901c84f21015b699cc40f6738ebc__COVAR_POP_examples1"/>

## Example

The following example measures the strength of association between employee age and salary. This function returns the value 73785.840059:

```
SELECT COVAR_POP( Salary, ( YEAR( NOW( ) ) - YEAR( BirthDate ) ) ) FROM Employees;
```

**Related Information**  


[COVAR_POP Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/6d40c8333876450388dfaa9078b06644.html "Returns the population covariance of a set of number pairs.") :arrow_upper_right:

