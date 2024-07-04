<!-- loio1af764816b5444808ebdd1d7a87d2518 -->

# REGR\_SXY Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

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



<a name="loio1af764816b5444808ebdd1d7a87d2518__section_iky_wf5_vrb"/>

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



<a name="loio1af764816b5444808ebdd1d7a87d2518__section_or5_xf5_vrb"/>

## Result Set

DOUBLE



<a name="loio1af764816b5444808ebdd1d7a87d2518__section_xfg_yf5_vrb"/>

## Remarks

This function converts its arguments to DOUBLE, performs the computation in double-precision floating-point, and returns a DOUBLE as the result. If applied to an empty set, then it returns NULL.

The function is applied to the set of \(dependent-expression and *<independent-expression\>*\) pairs after eliminating all pairs for which either dependent-expression or *<independent-expression\>* is NULL. The function is computed simultaneously during a single pass through the data. After eliminating NULL values, the following computation is made, where y represents the dependent-expression and x represents the *<independent-expression\>*:

```
REGR_COUNT(x, y) * COVAR_POP(x, y);
```

> ### Note:  
> ROLLUP and CUBE are not supported in the `GROUP BY` clause with Syntax 1. DISTINCT is not supported.

Syntax 2 – The *<window-spec\>* parameter represents usage as a window function in a `SELECT` statement. As such, you can specify elements of *<window-spec\>* either in the function syntax \(inline\), or with a `WINDOW` clause in the `SELECT` statement.



<a name="loio1af764816b5444808ebdd1d7a87d2518__section_vfx_yf5_vrb"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant. SQL/OLAP feature T612.
-   SAP database products – compatible with SAP SQL Anywhere



<a name="loio1af764816b5444808ebdd1d7a87d2518__section_hm3_zf5_vrb"/>

## Examples

The following example returns the value 5533938.004400015:

```
SELECT REGR_SXY( Salary, ( YEAR( NOW() ) - YEAR( BirthDate ) ) )FROM Employees;
```

**Related Information**  


[WINDOW Clause for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/window-clause-for-data-lake-relational-engine-sap-hana-db-managed-c83b61b.md "Defines all or part of a window for use with window functions such as AVG and RANK in a SELECT statement.")

[REGR_SYY Function \[Aggregate\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a57806cb84f21015933dc43a04d2cc9f.html "Returns values that can evaluate the statistical validity of a regression model.") :arrow_upper_right:

