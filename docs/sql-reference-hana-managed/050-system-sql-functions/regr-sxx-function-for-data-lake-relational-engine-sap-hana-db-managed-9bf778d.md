<!-- loio9bf778da26ef494686fbbecf7f2790b3 -->

# REGR\_SXX Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Computes the slope of the linear regression line, fitted to non-NULL pairs.




<dl>
<dt><b>

Syntax 1

</b></dt>
<dd>

```
REGR_SXX( <dependent-expression>, <independent-expression> )
```



</dd><dt><b>

Syntax 2

</b></dt>
<dd>

```
REGR_SXX( <dependent-expression>, <independent-expression> )
OVER ( <window-spec> )
```



</dd>
</dl>



<a name="loio9bf778da26ef494686fbbecf7f2790b3__section_pyv_kg5_vrb"/>

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



<a name="loio9bf778da26ef494686fbbecf7f2790b3__section_gk3_lg5_vrb"/>

## Returns

DOUBLE



<a name="loio9bf778da26ef494686fbbecf7f2790b3__section_why_lg5_vrb"/>

## Remarks

This function converts its arguments to DOUBLE, performs the computation in double-precision floating-point, and returns a DOUBLE as the result. If applied to an empty set, then `REGR_SXX` returns NULL.

The function is applied to the set of \(*<dependent-expression\>* and *<independent-expression\>*\) pairs after eliminating all pairs for which either *<dependent-expression\>* or *<independent-expression\>* is NULL. The function is computed simultaneously during a single pass through the data. After eliminating NULL values, the following computation is made, where *<y\>* represents the *<dependent-expression\>* and *<x\>* represents the *<independent-expression\>*:

```
REGR_COUNT(y, x) * VAR_POP(x)
```

> ### Note:  
> ROLLUP and CUBE are not supported in the `GROUP BY` clause with Syntax 1. DISTINCT is not supported.

Syntax 2 – The *<window-spec\>* parameter represents usage as a window function in a `SELECT` statement. As such, you can specify elements of *<window-spec\>* either in the function syntax \(inline\), or with a `WINDOW` clause in the `SELECT` statement.



<a name="loio9bf778da26ef494686fbbecf7f2790b3__section_gdt_phj_wrb"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant. SQL/OLAP feature T612.
-   SAP database products – compatible with SAP SQL Anywhere



<a name="loio9bf778da26ef494686fbbecf7f2790b3__section_kb4_ng5_vrb"/>

## Example

The following example returns the value 5916.4800000000105:

```
SELECT REGR_SXX( Salary, ( YEAR( NOW() ) - YEAR( BirthDate ) ) )FROM Employees;
```

**Related Information**  


[WINDOW Clause for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/window-clause-for-data-lake-relational-engine-sap-hana-db-managed-c83b61b.md "Defines all or part of a window for use with window functions such as AVG and RANK in a SELECT statement.")

[REGR_SXX Function [Aggregate] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a576c83284f21015b9d5bbf81742e83a.html "Computes the slope of the linear regression line, fitted to non-NULL pairs.") :arrow_upper_right:

