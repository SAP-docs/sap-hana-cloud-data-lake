<!-- loioa57806cb84f21015933dc43a04d2cc9f -->

# REGR\_SYY Function \[Aggregate\] for Data Lake Relational Engine

Returns values that can evaluate the statistical validity of a regression model.



 Syntax 1
 :   ```
REGR_SYY(<dependent-expression>, <independent-expression>)
```

  Syntax 2
 :   ```
REGR_SYY(<dependent-expression>, <independent-expression>)
OVER (<window-spec>)
```

 

<a name="loioa57806cb84f21015933dc43a04d2cc9f__REGR_SYY_parm1"/>

## Parameters

 *<dependent-expression\>*
 :   The variable that is affected by the independent variable.

  *<independent-expression\>*
 :   The variable that influences the outcome.

  *<window-spec\>*
 :   Specified when using this function as a window function.

 

<a name="loioa57806cb84f21015933dc43a04d2cc9f__REGR_SYY_returns1"/>

## Returns

DOUBLE



<a name="loioa57806cb84f21015933dc43a04d2cc9f__REGR_SYY_remarks1"/>

## Remarks

This function converts its arguments to DOUBLE, performs the computation in double-precision floating-point, and returns a DOUBLE as the result. If applied to an empty set, then `REGR_SYY` returns NULL.

The function is applied to the set of \(*<dependent-expression\>* and *<independent-expression\>*\) pairs after eliminating all pairs for which either *<dependent-expression\>* or *<independent-expression\>* is NULL. The function is computed simultaneously during a single pass through the data. After eliminating NULL values, the following computation is then made, where *<y\>* represents the *<dependent-expression\>* and *<x\>* represents the *<independent-expression\>*:

```
REGR_COUNT(x, y) * VAR_POP(y)
```

> ### Note:  
> ROLLUP and CUBE are not supported in the `GROUP BY` clause with Syntax 1. DISTINCT is not supported.

Syntax 2 – The *<window-spec\>* parameter represents usage as a window function in a `SELECT` statement. As such, you can specify elements of *<window-spec\>* either in the function syntax \(inline\), or with a `WINDOW` clause in the `SELECT` statement.



<a name="loioa57806cb84f21015933dc43a04d2cc9f__REGR_SYY_standards1"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant. SQL/OLAP feature T612.

-   SAP database products – compatible with SAP Adaptive Server Enterprise



<a name="loioa57806cb84f21015933dc43a04d2cc9f__REGR_SYY_example1"/>

## Example

The following example returns the value 26, 708, 672,843.3002:

```
SELECT REGR_SYY( Salary, ( YEAR( NOW() ) - YEAR( BirthDate ) ) )FROM Employees;
```

**Related Information**  


[Windowing Aggregate Function Usage in Data Lake Relational Engine](windowing-aggregate-function-usage-in-data-lake-relational-engine-a527f35.md "A major feature of the ISO/ANSI SQL extensions for OLAP is a construct called a window.")

[REGR_SYY Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/e582164fac45433190299553edc9fb6c.html "Returns values that can evaluate the statistical validity of a regression model.") :arrow_upper_right:

