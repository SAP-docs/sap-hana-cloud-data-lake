<!-- loio3a064918478c4d47ab0da64c2d61cc3e -->

# COVAR\_SAMP Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the sample covariance of a set of number pairs.




<dl>
<dt><b>

Syntax 1

</b></dt>
<dd>

```
COVAR_SAMP ( <dependent-expression>, <independent-expression> );
```



</dd><dt><b>

Syntax 2

</b></dt>
<dd>

```
COVAR_SAMP ( <dependent-expression>, <independent-expression> )
OVER ( <window-spec> );
```



</dd>
</dl>



<a name="loio3a064918478c4d47ab0da64c2d61cc3e__section_jny_wnl_srb"/>

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



<a name="loio3a064918478c4d47ab0da64c2d61cc3e__section_q44_xnl_srb"/>

## Remarks

This function converts its arguments to DOUBLE, performs the computation in double-precision floating-point, and returns a DOUBLE as the result. If applied to an empty set, then `COVAR_SAMP` returns NULL.

Both *<dependent-expression\>* and *<independent-expression\>* are numeric. The function is applied to the set of \(*<dependent-expression\>*, *<independent-expression\>*\) after eliminating the pairs for which either *<dependent-expression\>* or *<independent-expression\>* is NULL, where *<x\>* represents the *<dependent-expression\>* and *<y\>* represents the *<independent-expression\>*:

```
(SUM(x*y) - SUM(x) * SUM(y) / n) / (n-1);
```

> ### Note:  
> ROLLUP and CUBE are not supported in the `GROUP BY` clause with Syntax 1. DISTINCT is not supported.

Syntax 2 – The *<window-spec\>* parameter represents usage as a window function in a `SELECT` statement. As such, you can specify elements of *<window-spec\>* either in the function syntax \(inline\), or with a `WINDOW` clause in the `SELECT` statement.



<a name="loio3a064918478c4d47ab0da64c2d61cc3e__section_hrs_xfj_wrb"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant SQL foundation feature outside of core SQL.



<a name="loio3a064918478c4d47ab0da64c2d61cc3e__section_z4v_ynl_srb"/>

## Example

The following example measures the strength of association between employee age and salary. This function returns the value 74782.946005:

```
SELECT COVAR_SAMP( Salary, ( 2008 - YEAR( BirthDate ) ) ) FROM Employees;
```

**Related Information**  


[WINDOW Clause for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/window-clause-for-data-lake-relational-engine-sap-hana-db-managed-c83b61b.md "Defines all or part of a window for use with window functions such as AVG and RANK in a SELECT statement.")

[COVAR_SAMP Function \[Aggregate\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a5420eb484f21015be7f881364efd165.html "Returns the sample covariance of a set of number pairs.") :arrow_upper_right:

