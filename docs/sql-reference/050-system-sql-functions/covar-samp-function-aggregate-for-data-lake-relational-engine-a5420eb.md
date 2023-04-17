<!-- loioa5420eb484f21015be7f881364efd165 -->

# COVAR\_SAMP Function \[Aggregate\] for Data Lake Relational Engine

Returns the sample covariance of a set of number pairs.



 Syntax 1
 :   ```
COVAR_SAMP ( <dependent-expression>, <independent-expression> )
```

  Syntax 2
 :   ```
COVAR_SAMP ( <dependent-expression>, <independent-expression> )
OVER ( <window-spec> )
```

 

<a name="loioa5420eb484f21015be7f881364efd165__COVAR_SAMP_parm1"/>

## Parameters

 *<dependent-expression\>*
 :   The variable that is affected by the independent variable.

  *<independent-expression\>*
 :   The variable that influences the outcome.

  *<window-spec\>*
 :   Specified when using this function as a window function.

 

<a name="loioa5420eb484f21015be7f881364efd165__COVAR_SAMP_remarks1"/>

## Remarks

This function converts its arguments to DOUBLE, performs the computation in double-precision floating-point, and returns a DOUBLE as the result. If applied to an empty set, then `COVAR_SAMP` returns NULL.

Both *<dependent-expression\>* and *<independent-expression\>* are numeric. The function is applied to the set of \(*<dependent-expression\>*, *<independent-expression\>*\) after eliminating the pairs for which either *<dependent-expression\>* or *<independent-expression\>* is NULL, where *<x\>* represents the *<dependent-expression\>* and *<y\>* represents the *<independent-expression\>*:

```
(SUM(x*y) - SUM(x) * SUM(y) / n) / (n-1)
```

> ### Note:  
> ROLLUP and CUBE are not supported in the `GROUP BY` clause with Syntax 1. DISTINCT is not supported.

Syntax 2 – The *<window-spec\>* parameter represents usage as a window function in a `SELECT` statement. As such, you can specify elements of *<window-spec\>* either in the function syntax \(inline\), or with a `WINDOW` clause in the `SELECT` statement.



<a name="loioa5420eb484f21015be7f881364efd165__COVAR_SAMP_standards1"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant SQL foundation feature outside of core SQL.



<a name="loioa5420eb484f21015be7f881364efd165__COVAR_SAMP_examples1"/>

## Example

The following example measures the strength of association between employee age and salary. This function returns the value 74782.946005:

```
SELECT COVAR_SAMP( Salary, ( 2008 - YEAR( BirthDate ) ) ) FROM Employees;
```

**Related Information**  


[COVAR_SAMP Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/3a064918478c4d47ab0da64c2d61cc3e.html "Returns the sample covariance of a set of number pairs.") :arrow_upper_right:
