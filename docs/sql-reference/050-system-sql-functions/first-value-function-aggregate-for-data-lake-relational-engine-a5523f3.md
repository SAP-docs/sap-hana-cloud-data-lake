<!-- loioa5523f3c84f21015aa0092a61fcc2714 -->

# FIRST\_VALUE Function \[Aggregate\] for Data Lake Relational Engine

Returns the first value from a set of values.




<dl>
<dt><b>

Syntax 1: Windowed aggregate syntax

</b></dt>
<dd>

```
FIRST_VALUE (<expression> [IGNORE NULLS | RESPECT NULLS])
OVER (<window-spec>);
```



</dd><dt><b>

Syntax 2: Simple aggregate syntax

</b></dt>
<dd>

```
FIRST_VALUE (<input expression> [IGNORE NULLS | RESPECT NULLS] 
ORDER BY <ordering expression>);
```



</dd>
</dl>



<a name="loioa5523f3c84f21015aa0092a61fcc2714__FIRST_VALUE_parm1"/>

## Parameters


<table>
<tr>
<th valign="top" rowspan="1">

Parameter

</th>
<th valign="top" rowspan="1">

Description

</th>
</tr>
<tr>
<td valign="top" rowspan="1">

expression

</td>
<td valign="top" rowspan="1">

The expression on which to determine the first value in an ordered set.

</td>
</tr>
<tr>
<td valign="top">

input expression

</td>
<td valign="top">

Any scalar expression that results to a single column.

</td>
</tr>
<tr>
<td valign="top">

ordering expression

</td>
<td valign="top">

List of column names.

</td>
</tr>
</table>



<a name="loioa5523f3c84f21015aa0092a61fcc2714__FIRST_VALUE_returns1"/>

## Result Set

\(Syntax 1\) Data type of the values from the first row of a window.

\(Syntax 2\) Returns the value of the first element in *<input expression\>* as ordered by *<ordering expression\>*.



<a name="loioa5523f3c84f21015aa0092a61fcc2714__FIRST_VALUE_remarks1"/>

## Remarks

FIRST\_VALUE returns the first value in a set of values, which is usually an ordered set. If the first value in the set is null, then the function returns NULL unless you specify IGNORE NULLS. If you specify IGNORE NULLS, then FIRST\_VALUE returns the first non-null value in the set, or NULL if all values are null.

The data type of the returned value is the same as that of the input value.

You cannot use FIRST\_VALUE or any other analytic function for expression. That is, you cannot nest analytic functions, but you can use other built-in function expressions for expression.

If the windowed aggregate syntax *<window-spec\>* does not contain an ORDER BY expression, or if the ORDER BY expression is not precise enough to guarantee a unique ordering, then the result is arbitrary. If there is no *<window-spec\>*, then the result is arbitrary.

You can specify elements of *<window-spec\>* either in the function syntax \(inline\), or with a WINDOW clause in the SELECT statement.

> ### Note:  
> DISTINCT is not supported.



<a name="loioa5523f3c84f21015aa0092a61fcc2714__FIRST_VALUE_standards1"/>

## Standards and Compatibility

-   SQL—ISO/ANSI SQL compliant. SQL/OLAP feature T612.




<a name="loioa5523f3c84f21015aa0092a61fcc2714__FIRST_VALUE_example1"/>

## Examples

-   This returns the relationship, expressed as a percentage, between each employee’s salary and that of the most recently hired employee in the same department:

    ```
    SELECT DepartmentID, EmployeeID,
    100 * Salary / ( FIRST_VALUE( Salary ) OVER (
    PARTITION BY DepartmentID  
    ORDER BY Year(StartDate) DESC ) )
    AS percentage
    FROM Employees order by DepartmentID DESC;
    ```

    The returned result set is:


    <table>
    <tr>
    <th valign="top" rowspan="1">

    DepartmentID
    
    </th>
    <th valign="top" rowspan="1">

    EmployeeID
    
    </th>
    <th valign="top" rowspan="1">

    Percentage
    
    </th>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    500
    
    </td>
    <td valign="top" rowspan="1">
    
    1,658
    
    </td>
    <td valign="top" rowspan="1">
    
    100.000000000000000000000
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    500
    
    </td>
    <td valign="top" rowspan="1">
    
    1,570
    
    </td>
    <td valign="top" rowspan="1">
    
    138.842709713689113761394
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    500
    
    </td>
    <td valign="top" rowspan="1">
    
    1,615
    
    </td>
    <td valign="top" rowspan="1">
    
    110.428462434244870095972
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    500
    
    </td>
    <td valign="top" rowspan="1">
    
    1,013
    
    </td>
    <td valign="top" rowspan="1">
    
    109.585190539292454724330
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    500
    
    </td>
    <td valign="top" rowspan="1">
    
    750
    
    </td>
    <td valign="top" rowspan="1">
    
    137.734409508894510701521
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    500
    
    </td>
    <td valign="top" rowspan="1">
    
    921
    
    </td>
    <td valign="top" rowspan="1">
    
    167.449704854836766654619
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    500
    
    </td>
    <td valign="top" rowspan="1">
    
    868
    
    </td>
    <td valign="top" rowspan="1">
    
    113.239368750752921334778
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    500
    
    </td>
    <td valign="top" rowspan="1">
    
    703
    
    </td>
    <td valign="top" rowspan="1">
    
    222.867927558928643135365
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    500
    
    </td>
    <td valign="top" rowspan="1">
    
    191
    
    </td>
    <td valign="top" rowspan="1">
    
    119.664297474199895594908
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    400
    
    </td>
    <td valign="top" rowspan="1">
    
    1,684
    
    </td>
    <td valign="top" rowspan="1">
    
    100.000000000000000000000
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    400
    
    </td>
    <td valign="top" rowspan="1">
    
    1,740
    
    </td>
    <td valign="top" rowspan="1">
    
    76.128652163477274215016
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    400
    
    </td>
    <td valign="top" rowspan="1">
    
    1,751
    
    </td>
    <td valign="top" rowspan="1">
    
    76.353400685155687446813
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    400
    
    </td>
    <td valign="top" rowspan="1">
    
    1,607
    
    </td>
    <td valign="top" rowspan="1">
    
    133.758100765890593292456
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    400
    
    </td>
    <td valign="top" rowspan="1">
    
    1,507
    
    </td>
    <td valign="top" rowspan="1">
    
    77.996465120338650199655
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="1">
    
    400
    
    </td>
    <td valign="top" rowspan="1">
    
    1,576
    
    </td>
    <td valign="top" rowspan="1">
    
    150.428767810774836893669
    
    </td>
    </tr>
    </table>
    
    In this example, employee 1658 is the first row for department 500, indicating that employee 1658 is the most recent hire in that department, and therefore receives a percentage of 100 percent. Percentages for the remaining employees in department 500 are calculated relative to that of employee 1658. For example, employee 1570 earns approximately 139 percent of what employee 1658 earns.

-   This example uses the simple aggregate function syntax:

    ```
    SELECT FIRST_VALUE (COL1 ORDER BY COL2) from T1
    SELECT FIRST_VALUE (COL1+COL2 ORDER BY COL3, COL4) from T1 
    SELECT FIRST_VALUE (COL1+2 ORDER BY COL2) from T1;
    ```


**Related Information**  


[Windowing Aggregate Function Usage in Data Lake Relational Engine](windowing-aggregate-function-usage-in-data-lake-relational-engine-a527f35.md "A major feature of the ISO/ANSI SQL extensions for OLAP is a construct called a window.")

[FIRST_VALUE Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/9994e0a4b12c4073a74b5a37d5e25f2e.html "Returns the first value from a set of values.") :arrow_upper_right:

