<!-- loioa562edfc84f210159175c2831fabbd47 -->

# MEDIAN Function \[Aggregate\] for Data Lake Relational Engine

Returns the median of an expression.




<dl>
<dt><b>

Syntax 1

</b></dt>
<dd>

```
MEDIAN ( [ ALL | DISTINCT ] <expression> );
```



</dd><dt><b>

Syntax 2

</b></dt>
<dd>

```
MEDIAN ( [ ALL | DISTINCT ] <expression> )
OVER ( <window-spec> );
```



</dd>
</dl>



<a name="loioa562edfc84f210159175c2831fabbd47__MEDIAN_parm1"/>

## Parameters


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

A numeric expression for which a median value is to be computed.



</dd><dt><b>

*<window-spec\>*

</b></dt>
<dd>

Specified when using this function as a window function.



</dd>
</dl>



<a name="loioa562edfc84f210159175c2831fabbd47__MEDIAN_remarks1"/>

## Remarks

The median is the number separating the higher half of a sample, a population, or a probability distribution, from the lower half.

The data type of the returned value is the same as that of the input value. NULLs are ignored in the calculation of the median value. You can use the optional keyword DISTINCT to eliminate duplicate values before the aggregate function is applied. `ALL`, which performs the operation on all rows, is the default.

> ### Note:  
> ROLLUP and CUBE are not supported in the GROUP BY clause with Syntax 1.

Syntax 2 – The *<window-spec\>* parameter represents usage as a window function in a `SELECT` statement. As such, you can specify elements of *<window-spec\>* either in the function syntax \(inline\), or with a `WINDOW` clause in the `SELECT` statement.

> ### Note:  
> The *<window-spec\>* cannot contain a ROW, RANGE or ORDER BY specification; *<window-spec\>* can only specify a PARTITION clause. DISTINCT is not supported if a WINDOW clause is used.



<a name="loioa562edfc84f210159175c2831fabbd47__MEDIAN_standards1"/>

## Standards and Compatibility

SQL – Transact-SQL extension to ISO/ANSI SQL grammar



<a name="loioa562edfc84f210159175c2831fabbd47__MEDIAN_example1"/>

## Examples

The following query returns the median salary for each department in Florida:

```
SELECT DepartmentID, Surname, Salary,
MEDIAN(Salary) OVER (PARTITION BY DepartmentID) "Median"
FROM Employees
WHERE State IN ('FL');
```

The returned result is:


<table>
<tr>
<th valign="top" rowspan="1">

DepartmentID

</th>
<th valign="top" rowspan="1">

Surname

</th>
<th valign="top" rowspan="1">

Salary

</th>
<th valign="top" rowspan="1">

Median

</th>
</tr>
<tr>
<td valign="top" rowspan="1">

100

</td>
<td valign="top" rowspan="1">

Lull

</td>
<td valign="top" rowspan="1">

87,900.000

</td>
<td valign="top" rowspan="1">

73,870.000

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

100

</td>
<td valign="top" rowspan="1">

Gowda

</td>
<td valign="top" rowspan="1">

59,840.000

</td>
<td valign="top" rowspan="1">

73,870.000

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

200

</td>
<td valign="top" rowspan="1">

Sterling

</td>
<td valign="top" rowspan="1">

64,900.000

</td>
<td valign="top" rowspan="1">

76,200.000

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

200

</td>
<td valign="top" rowspan="1">

Kelly

</td>
<td valign="top" rowspan="1">

87,500.000

</td>
<td valign="top" rowspan="1">

76,200.000

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

300

</td>
<td valign="top" rowspan="1">

Litton

</td>
<td valign="top" rowspan="1">

58,930.000

</td>
<td valign="top" rowspan="1">

58,930.000

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

400

</td>
<td valign="top" rowspan="1">

Francis

</td>
<td valign="top" rowspan="1">

53,870.000

</td>
<td valign="top" rowspan="1">

38,70.000

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

400

</td>
<td valign="top" rowspan="1">

Charlton

</td>
<td valign="top" rowspan="1">

28,300.000

</td>
<td valign="top" rowspan="1">

53,870.000

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

400

</td>
<td valign="top" rowspan="1">

Evans

</td>
<td valign="top" rowspan="1">

68,940.000

</td>
<td valign="top" rowspan="1">

53,870.000

</td>
</tr>
</table>

**Related Information**  


[Windowing Aggregate Function Usage in Data Lake Relational Engine](windowing-aggregate-function-usage-in-data-lake-relational-engine-a527f35.md "A major feature of the ISO/ANSI SQL extensions for OLAP is a construct called a window.")

[MEDIAN Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/d48698c99cd5450980130ce6dcd32356.html "Returns the median of an expression.") :arrow_upper_right:

