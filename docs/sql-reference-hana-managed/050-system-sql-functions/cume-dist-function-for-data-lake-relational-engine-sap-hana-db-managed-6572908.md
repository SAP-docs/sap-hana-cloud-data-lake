<!-- loio65729084257448758370d2196d0f1021 -->

# CUME\_DIST Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

The `CUME_DIST` function is a rank analytical function that calculates the relative position of one value among a group of rows. It returns a decimal value between 0 and 1.



```
CUME_DIST () OVER (<window-spec>);
```



<a name="loio65729084257448758370d2196d0f1021__section_ivf_tml_srb"/>

## Parameters


<dl>
<dt><b>

*<window-spec\>*

</b></dt>
<dd>

Specified when using this function as a window function.



</dd>
</dl>



<a name="loio65729084257448758370d2196d0f1021__section_lbv_tml_srb"/>

## Result Set

A DOUBLE value between 0 and 1.



<a name="loio65729084257448758370d2196d0f1021__section_thk_5ml_srb"/>

## Remarks

Data lake Relational Engine calculates the cumulative distribution of a value of x in a set S of size N using CUME\_DIST\(x\) = number of values in S coming before and including x in the specified order / N

Composite sort-keys are not currently allowed in the CUME\_DIST function. You can use composite sort-keys with any of the other rank functions.

The *<window-spec\>* parameter represents usage as a window function in a `SELECT` statement. As such, you can specify elements of *<window-spec\>* either in the function syntax \(inline\), or with a `WINDOW` clause in the `SELECT` statement. The *<window-spec\>* must contain the `ORDER BY` clause, and cannot contain a `ROWS` or `RANGE` clause.

> ### Note:  
> DISTINCT is not supported.



<a name="loio65729084257448758370d2196d0f1021__section_m2z_5ml_srb"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant. SQL feature T612.



<a name="loio65729084257448758370d2196d0f1021__section_vq2_wml_srb"/>

## Example

The following example returns a result set that provides a cumulative distribution of the salaries of employees who live in California:

```
SELECT DepartmentID, Surname, Salary,
              CUME_DIST() OVER (PARTITION BY DepartmentID
              ORDER BY Salary DESC) "Rank"
              FROM Employees WHERE State IN ('CA');
```

The returned result set is:


<table>
<tr>
<th valign="top">

DepartmentID

</th>
<th valign="top">

Surname

</th>
<th valign="top">

Salary

</th>
<th valign="top">

Rank

</th>
</tr>
<tr>
<td valign="top">

200

</td>
<td valign="top">

Savarino

</td>
<td valign="top">

72,300.000

</td>
<td valign="top">

0.333333

</td>
</tr>
<tr>
<td valign="top">

200

</td>
<td valign="top">

Clark

</td>
<td valign="top">

45,000.000

</td>
<td valign="top">

0.666667

</td>
</tr>
<tr>
<td valign="top">

200

</td>
<td valign="top">

Overbey

</td>
<td valign="top">

39,300.000

</td>
<td valign="top">

1.000000

</td>
</tr>
</table>

**Related Information**  


[WINDOW Clause for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/window-clause-for-data-lake-relational-engine-sap-hana-db-managed-c83b61b.md "Defines all or part of a window for use with window functions such as AVG and RANK in a SELECT statement.")

[CUME_DIST Function \[Analytical\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a54314be84f210159603ce84a892876c.html "The CUME_DIST function is a rank analytical function that calculates the relative position of one value among a group of rows. It returns a decimal value between 0 and 1.") :arrow_upper_right:

