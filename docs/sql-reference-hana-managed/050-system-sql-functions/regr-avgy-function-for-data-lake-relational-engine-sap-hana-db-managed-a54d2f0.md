<!-- loioa54d2f0bde2f44d6bb973767b6fc47f4 -->

# REGR\_AVGY Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Computes the average of the dependent variable of the regression line.




<dl>
<dt><b>

Syntax 1

</b></dt>
<dd>

```
REGR_AVGY( <dependent-expression>, <independent-expression> );
```



</dd><dt><b>

Syntax 2

</b></dt>
<dd>

```
REGR_AVGY( <dependent-expression>, <independent-expression> )
OVER ( <window-spec> );
```



</dd>
</dl>



<a name="loioa54d2f0bde2f44d6bb973767b6fc47f4__section_vq1_gn3_wrb"/>

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



<a name="loioa54d2f0bde2f44d6bb973767b6fc47f4__section_d3j_3j5_vrb"/>

## Result Set

DOUBLE



<a name="loioa54d2f0bde2f44d6bb973767b6fc47f4__section_c3c_1k5_vrb"/>

## Remarks

This function converts its arguments to DOUBLE, performs the computation in double-precision floating-point, and returns a DOUBLE as the result. If applied to an empty set, then `REGR_AVGY` returns NULL.

The function is applied to the set of \(*<dependent-expression\>* and *<dependent-expression\>*\) pairs after eliminating all pairs for which either *<dependent-expression\>* or *<dependent-expression\>* is NULL. The function is computed simultaneously during a single pass through the data. After eliminating NULL values, the following computation is then made, where *<y\>* represents the *<dependent-expression\>*:

```
AVG(y);
```

> ### Note:  
> ROLLUP and CUBE are not supported in the `GROUP BY` clause with Syntax 1. DISTINCT is not supported.

Syntax 2 – The *<window-spec\>* parameter represents usage as a window function in a `SELECT` statement. As such, you can specify elements of *<window-spec\>* either in the function syntax \(inline\), or with a `WINDOW` clause in the `SELECT` statement.



<a name="loioa54d2f0bde2f44d6bb973767b6fc47f4__section_nkr_1k5_vrb"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant. SQL/OLAP feature T612.
-   SAP database products – compatible with SAP SQL Anywhere



<a name="loioa54d2f0bde2f44d6bb973767b6fc47f4__section_g5f_bk5_vrb"/>

## Examples

The following example calculates the average of the independent variable, employee salary:

```
SELECT REGR_AVGY( Salary, ( YEAR( NOW( )) - YEAR( BirthDate ) ) )FROM Employees;
```

This function returns the value 49988.6232.

**Related Information**  


[WINDOW Clause for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/window-clause-for-data-lake-relational-engine-sap-hana-db-managed-c83b61b.md "Defines all or part of a window for use with window functions such as AVG and RANK in a SELECT statement.")

[REGR_AVGY Function \[Aggregate\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a574426e84f210159d5d8adecd1f70f2.html "Computes the average of the dependent variable of the regression line.") :arrow_upper_right:

