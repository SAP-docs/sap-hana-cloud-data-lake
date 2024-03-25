<!-- loioa57748fd84f21015bfd08e9110638b53 -->

# REGR\_SXY Function \[Aggregate\] for Data Lake Relational Engine

Returns the sum of products of the dependent and independent variables. Use REGR\_SXY to evaluate the statistical validity of a regression model.




<dl>
<dt><b>

Syntax 1

</b></dt>
<dd>

```
REGR_SXY( <dependent-expression>, <independent-expression> );
```



</dd><dt><b>

Syntax 2

</b></dt>
<dd>

```
REGR_SXY( <dependent-expression>, <independent-expression> )
OVER ( <window-spec> );
```



</dd>
</dl>



<a name="loioa57748fd84f21015bfd08e9110638b53__REGR_SXY_parm1"/>

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



<a name="loioa57748fd84f21015bfd08e9110638b53__REGR_SXY_returns1"/>

## Result Set

DOUBLE



<a name="loioa57748fd84f21015bfd08e9110638b53__REGR_SXY_remarks1"/>

## Remarks

This function converts its arguments to DOUBLE, performs the computation in double-precision floating-point, and returns a DOUBLE as the result. If applied to an empty set, then it returns NULL.

The function is applied to the set of \(dependent-expression and *<independent-expression\>*\) pairs after eliminating all pairs for which either dependent-expression or *<independent-expression\>* is NULL. The function is computed simultaneously during a single pass through the data. After eliminating NULL values, the following computation is made, where y represents the dependent-expression and x represents the *<independent-expression\>*:

```
REGR_COUNT(x, y) * COVAR_POP(x, y);
```

> ### Note:  
> ROLLUP and CUBE are not supported in the `GROUP BY` clause with Syntax 1. DISTINCT is not supported.

Syntax 2 – The *<window-spec\>* parameter represents usage as a window function in a `SELECT` statement. As such, you can specify elements of *<window-spec\>* either in the function syntax \(inline\), or with a `WINDOW` clause in the `SELECT` statement.



<a name="loioa57748fd84f21015bfd08e9110638b53__REGR_SXY_standards1"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant. SQL/OLAP feature T612.
-   SAP database products – compatible with SAP SQL Anywhere



<a name="loioa57748fd84f21015bfd08e9110638b53__REGR_SXY_example1"/>

## Example

The following example returns the value 5533938.004400015:

```
SELECT REGR_SXY( Salary, ( YEAR( NOW() ) - YEAR( BirthDate ) ) )FROM Employees;
```

**Related Information**  


[Windowing Aggregate Function Usage in Data Lake Relational Engine](windowing-aggregate-function-usage-in-data-lake-relational-engine-a527f35.md "A major feature of the ISO/ANSI SQL extensions for OLAP is a construct called a window.")

[REGR_SXY Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/1af764816b5444808ebdd1d7a87d2518.html "Returns the sum of products of the dependent and independent variables. Use REGR_SXY to evaluate the statistical validity of a regression model.") :arrow_upper_right:

