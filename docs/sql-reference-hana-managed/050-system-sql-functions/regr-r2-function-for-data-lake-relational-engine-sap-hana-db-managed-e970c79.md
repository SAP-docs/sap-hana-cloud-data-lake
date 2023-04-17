<!-- loioe970c79f12d44021b872f41c9f5ce7d9 -->

# REGR\_R2 Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Computes the coefficient of determination \(also referred to as R-squared or the goodness-of-fit statistic\) for the regression line.



 Syntax 1
 :   ```
REGR_R2( <dependent-expression>, <independent-expression> )
```

  Syntax 2
 :   ```
REGR_R2( <dependent-expression>, <independent-expression> )
OVER ( <window-spec> )
```

 

<a name="loioe970c79f12d44021b872f41c9f5ce7d9__section_rpl_rh5_vrb"/>

## Parameters

 *<dependent-expression\>*
 :   The variable that is affected by the independent variable.

  *<independent-expression\>*
 :   The variable that influences the outcome.

  *<window-spec\>*
 :   Specified when using this function as a window function.

 

<a name="loioe970c79f12d44021b872f41c9f5ce7d9__section_ejv_rh5_vrb"/>

## Returns

DOUBLE



<a name="loioe970c79f12d44021b872f41c9f5ce7d9__section_a4k_sh5_vrb"/>

## Remarks

This function converts its arguments to DOUBLE, performs the computation in double-precision floating-point, and returns a DOUBLE as the result. If applied to an empty set, then `REGR_R2` returns NULL.

`REGR_R2` is applied to the set of \(*<dependent-expression\>* and *<independent-expression\>*\) pairs after eliminating all pairs for which either *<dependent-expression\>* or *<independent-expression\>* is NULL. Data lake Relational Engine then applies the following algorithm, where *<y\>* represents the *<dependent-expression\>* and *<x\>* represents the *<independent-expression\>*:

-   `REGR_R2` calculates `VAR_POP(x)` and returns NULL if `VAR_POP(x) = 0`; otherwise, it calculates `VAR_POP(y)` and returns the value 1 if `VAR_POP(y) = 0`.
-   If neither `VAR_POP(x)` or `VAR_POP(y)` is zero, the return value is `POWER(CORR(y,x),2)`.

> ### Note:  
> ROLLUP and CUBE are not supported in the `GROUP BY` clause with Syntax 1. `DISTINCT` is not supported.

Syntax 2 – The *<window-spec\>* parameter represents usage as a window function in a `SELECT` statement. As such, you can specify elements of *<window-spec\>* either in the function syntax \(inline\), or with a `WINDOW` clause in the `SELECT` statement.



<a name="loioe970c79f12d44021b872f41c9f5ce7d9__section_chj_th5_vrb"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant. SQL/OLAP feature T612.
-   SAP database products – compatible with SAP SQL Anywhere



<a name="loioe970c79f12d44021b872f41c9f5ce7d9__section_js5_th5_vrb"/>

## Example

The following example returns the value 0.19379959710325653:

```
SELECT REGR_R2( Salary, ( YEAR( NOW() ) - YEAR( BirthDate ) ) )FROM Employees;
```

**Related Information**  


[WINDOW Clause for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/window-clause-for-data-lake-relational-engine-sap-hana-db-managed-c83b61b.md "Defines all or part of a window for use with window functions such as AVG and RANK in a SELECT statement.")

[REGR_R2 Function [Aggregate] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a575c77684f210158d23e68bbd456148.html "Computes the coefficient of determination (also referred to as R-squared or the goodness-of-fit statistic) for the regression line.") :arrow_upper_right:

