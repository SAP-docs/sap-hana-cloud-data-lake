<!-- loio8cf5191242464c6bb1965cbb657bdab1 -->

# LAST\_VALUE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the last value from a set of values.



**Syntax 1**

Windowed aggregate syntax.

```
LAST_VALUE (<expression> [IGNORE NULLS | RESPECT NULLS])
OVER (<window-spec>)
```

**Syntax 2**

Simple aggregate syntax.

```
LAST_VALUE (<input expression> [IGNORE NULLS | RESPECT NULLS] 
ORDER BY <ordering expression>)
```



<a name="loio8cf5191242464c6bb1965cbb657bdab1__section_olw_t2h_trb"/>

## Parameters


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

The expression on which to determine the last value in an ordered set.



</dd><dt><b>

*<window\_spec\>*

</b></dt>
<dd>

Specified when using this function as a window function.



</dd><dt><b>

*<input\_expression\>*

</b></dt>
<dd>

Any scalar expression that results to a single column.



</dd><dt><b>

*<ordering\_expression\>*

</b></dt>
<dd>

List of column names.



</dd>
</dl>



<a name="loio8cf5191242464c6bb1965cbb657bdab1__section_ojw_52h_trb"/>

## Returns

\(Syntax 1\) Returns the data type of the argument.

\(Syntax 2\) Returns the value of the last element in *<input expression\>* as ordered by *<ordering expression\>*.



<a name="loio8cf5191242464c6bb1965cbb657bdab1__section_wll_v2h_trb"/>

## Remarks

LAST\_VALUE returns the last value in a set of values, which is usually an ordered set. If the last value in the set is null, then the function returns NULL unless you specify IGNORE NULLS. If you specify IGNORE NULLS, then LAST\_VALUE returns the last non-null value in the set, or NULL if all values are null.

The data type of the returned value is the same as that of the input value.

You cannot use LAST\_VALUE or any other analytic function for expression. That is, you cannot nest analytic functions, but you can use other built-in function expressions for expression.

If the windowed-aggregate syntax *<window-spec\>* does not contain an ORDER BY expression, or if the ORDER BY expression is not precise enough to guarantee a unique ordering, then the result is arbitrary. If there is no *<window-spec\>*, then the result is arbitrary.

You can specify elements of *<window-spec\>* either in the function syntax \(inline\), or with a WINDOW clause in the SELECT statement.

> ### Note:  
> DISTINCT is not supported.



<a name="loio8cf5191242464c6bb1965cbb657bdab1__section_pt1_w2h_trb"/>

## Standards and Compatibility

-   SQL—ISO/ANSI SQL compliant. SQL/OLAP feature T612.




**Example 1**

This example returns the salary of each employee, plus the name of the employee with the highest salary in their department:

```
SELECT GivenName + ' ' + Surname AS employee_name, 
	Salary, DepartmentID,
	LAST_VALUE( employee_name ) OVER Salary_Window AS highest_paid
FROM Employees
WINDOW Salary_Window AS ( PARTITION BY DepartmentID ORDER BY Salary 
	RANGE BETWEEN UNBOUNDED PRECEDING 
	AND UNBOUNDED FOLLOWING )
ORDER BY DepartmentID DESC;
```

The returned result set is:


<table>
<tr>
<th valign="top" rowspan="1">

employee\_name



</th>
<th valign="top" rowspan="1">

Salary



</th>
<th valign="top" rowspan="1">

DepartmentID



</th>
<th valign="top" rowspan="1">

highest\_paid



</th>
</tr>
<tr>
<td valign="top" rowspan="1">

Michael Lynch



</td>
<td valign="top" rowspan="1">

24,903.000



</td>
<td valign="top" rowspan="1">

500



</td>
<td valign="top" rowspan="1">

Juan Martinez



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

Juanph Barker



</td>
<td valign="top" rowspan="1">

27,290.000



</td>
<td valign="top" rowspan="1">

500



</td>
<td valign="top" rowspan="1">

Juan Martinez



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

Sheila Romero



</td>
<td valign="top" rowspan="1">

27,500.000



</td>
<td valign="top" rowspan="1">

500



</td>
<td valign="top" rowspan="1">

Juan Martinez



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

Felicia Kuo



</td>
<td valign="top" rowspan="1">

28,200.000



</td>
<td valign="top" rowspan="1">

500



</td>
<td valign="top" rowspan="1">

Juan Martinez



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

Jeannette Bertrand



</td>
<td valign="top" rowspan="1">

29,800.000



</td>
<td valign="top" rowspan="1">

500



</td>
<td valign="top" rowspan="1">

Juan Martinez



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

Jane Braun



</td>
<td valign="top" rowspan="1">

34,300.000



</td>
<td valign="top" rowspan="1">

500



</td>
<td valign="top" rowspan="1">

Juan Martinez



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

Anthony Rebeiro



</td>
<td valign="top" rowspan="1">

34,576.000



</td>
<td valign="top" rowspan="1">

500



</td>
<td valign="top" rowspan="1">

Juan Martinez



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

Charles Crowley



</td>
<td valign="top" rowspan="1">

41,700.000



</td>
<td valign="top" rowspan="1">

500



</td>
<td valign="top" rowspan="1">

Juan Martinez



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

Juan Martinez



</td>
<td valign="top" rowspan="1">

55,500.800



</td>
<td valign="top" rowspan="1">

500



</td>
<td valign="top" rowspan="1">

Juan Martinez



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

Doug Charlton



</td>
<td valign="top" rowspan="1">

28,300.000



</td>
<td valign="top" rowspan="1">

400



</td>
<td valign="top" rowspan="1">

Scott Evans



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

Elizabeth Lambert



</td>
<td valign="top" rowspan="1">

29,384.000



</td>
<td valign="top" rowspan="1">

400



</td>
<td valign="top" rowspan="1">

Scott Evans



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

Joyce Butterfield



</td>
<td valign="top" rowspan="1">

34,011.000



</td>
<td valign="top" rowspan="1">

400



</td>
<td valign="top" rowspan="1">

Scott Evans



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

Robert Nielsen



</td>
<td valign="top" rowspan="1">

34,889.000



</td>
<td valign="top" rowspan="1">

400



</td>
<td valign="top" rowspan="1">

Scott Evans



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

Alex Ahmed



</td>
<td valign="top" rowspan="1">

34,992.000



</td>
<td valign="top" rowspan="1">

400



</td>
<td valign="top" rowspan="1">

Scott Evans



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

Ruth Wetherby



</td>
<td valign="top" rowspan="1">

35,745.000



</td>
<td valign="top" rowspan="1">

400



</td>
<td valign="top" rowspan="1">

Scott Evans



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

...



</td>
<td valign="top" rowspan="1">

...



</td>
<td valign="top" rowspan="1">

...



</td>
<td valign="top" rowspan="1">

...



</td>
</tr>
</table>

**Example 2**

This example uses the simple aggregate function syntax:

```
SELECT LAST_VALUE (COL1 ORDER BY COL2) from T1
SELECT LAST_VALUE (COL1+COL2 ORDER BY COL3, COL4) from T1 
SELECT LAST_VALUE (COL1+2 ORDER BY COL2) from T1
```

**Related Information**  


[WINDOW Clause for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/window-clause-for-data-lake-relational-engine-sap-hana-db-managed-c83b61b.md "Defines all or part of a window for use with window functions such as AVG and RANK in a SELECT statement.")

[LAST_VALUE Function [Aggregate] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a55bfa7784f21015b86bd5dcfa28a6a5.html "Returns the last value from a set of values.") :arrow_upper_right:

