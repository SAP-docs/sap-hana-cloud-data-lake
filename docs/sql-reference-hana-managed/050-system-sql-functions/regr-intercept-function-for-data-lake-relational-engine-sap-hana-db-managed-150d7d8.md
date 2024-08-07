<!-- loio150d7d8e1d9a456a867139f014feba18 -->

# REGR\_INTERCEPT Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Computes the `y`-intercept of the linear regression line that best fits the dependent and independent variables.




<dl>
<dt><b>

Syntax 1

</b></dt>
<dd>

```
REGR_INTERCEPT( <dependent-expression>, <independent-expression> );
```



</dd><dt><b>

Syntax 2

</b></dt>
<dd>

```
REGR_INTERCEPT( <dependent-expression>, <independent-expression> )
OVER ( <window-spec> );
```



</dd>
</dl>



<a name="loio150d7d8e1d9a456a867139f014feba18__section_kfg_f35_vrb"/>

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



<a name="loio150d7d8e1d9a456a867139f014feba18__section_mxq_f35_vrb"/>

## Result Set

DOUBLE



<a name="loio150d7d8e1d9a456a867139f014feba18__section_n1f_g35_vrb"/>

## Remarks

This function converts its arguments to DOUBLE, performs the computation in double-precision floating-point, and returns a DOUBLE as the result. If applied to an empty set, `REGR_INTERCEPT` returns NULL.

The function is applied to the set of \(*<dependent-expression\>* and *<independent-expression\>*\) pairs after eliminating all pairs for which either *<dependent-expression\>* or *<independent-expression\>* is NULL. The function is computed simultaneously during a single pass through the data. After eliminating NULL values, the following computation is made, where *<y\>* represents the *<dependent-expression\>* and *<x\>* represents the *<independent-expression\>*:

```
AVG(y) - REGR_SLOPE(y, x) * AVG(x);
```

> ### Note:  
> ROLLUP and CUBE are not supported in the `GROUP BY` clause with Syntax 1. DISTINCT is not supported.

Syntax 2 – The *<window-spec\>* parameter represents usage as a window function in a `SELECT` statement. As such, you can specify elements of *<window-spec\>* either in the function syntax \(inline\), or with a `WINDOW` clause in the `SELECT` statement.



<a name="loio150d7d8e1d9a456a867139f014feba18__section_try_g35_vrb"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant. SQL/OLAP feature T612.
-   SAP database products – compatible with SAP SQL Anywhere



<a name="loio150d7d8e1d9a456a867139f014feba18__section_m3j_h35_vrb"/>

## Examples

The following example returns the value 1874.5805688517603:

```
SELECT REGR_INTERCEPT( Salary, ( YEAR( NOW() ) - YEAR( BirthDate ) ) )FROM Employees;
```

**Related Information**  


[WINDOW Clause for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/window-clause-for-data-lake-relational-engine-sap-hana-db-managed-c83b61b.md "Defines all or part of a window for use with window functions such as AVG and RANK in a SELECT statement.")

[REGR_INTERCEPT Function \[Aggregate\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a57548bd84f21015a72397703df578ba.html "Computes the y-intercept of the linear regression line that best fits the dependent and independent variables.") :arrow_upper_right:

