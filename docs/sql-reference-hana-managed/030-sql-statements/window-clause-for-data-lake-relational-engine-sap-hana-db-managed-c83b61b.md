<!-- loioc83b61b2b1814dbeaafa016b209a2d4d -->

# WINDOW Clause for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Defines all or part of a window for use with window functions such as AVG and RANK in a SELECT statement.



<a name="loioc83b61b2b1814dbeaafa016b209a2d4d__section_wpz_x2x_vbc"/>

## Usage

This SQL statement clause can only be used within the SELECT statement.



```
WINDOW <window-expression>, ...
```

```
<window-expression> : <new-window-name> AS ( <window-spec> )
```

```
<window-spec> :
[ <existing-window-name> ]
[ PARTITION BY <expression>, ... ]
[ ORDER BY <expression> [ ASC | DESC ], ... ]
[ { ROWS | RANGE } { <window-frame-start> | <window-frame-between> } ] 
```

```
<window-frame-start> :
{ UNBOUNDED PRECEDING
 | <unsigned-integer> PRECEDING
 | CURRENT ROW }
```

```
<window-frame-between> :
BETWEEN <window-frame-bound1> AND <window-frame-bound2>
```

```
<window-frame-bound> :
<window-frame-start>
| UNBOUNDED FOLLOWING 
| <unsigned-integer> FOLLOWING
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioc83b61b2b1814dbeaafa016b209a2d4d__section_afh_z2x_vbc"/>

## Parameters


<dl class="glossary">
<dt><b>

PARTITION BY clause

</b></dt>
<dd>

The PARTITION BY clause organizes the result set into logical groups based on the unique values of the specified expression. When this clause is used with window functions, the functions are applied to each partition independently. For example, if you follow PARTITION BY with a column name, the result set is partitioned by distinct values in the column.

If this clause is omitted, the entire result set is considered a partition.

The PARTITION BY *<expression\>* cannot be an integer literal.



</dd><dt><b>

ORDER BY clause

</b></dt>
<dd>

The ORDER BY clause defines how to sort the rows in each partition of the result set. You can further control the order by specifying ASC for ascending order \(the default\) or DESC for descending order.

The ORDER BY *<expression\>* cannot be an integer literal.

If this clause is omitted, the database server returns rows in whatever order is most efficient, and the appearance of result sets may vary depending on when you last accessed the row.



</dd><dt><b>

ROWS clause and RANGE clause

</b></dt>
<dd>

Use either a ROWS or RANGE clause to express the size of the window. The window size can be one, many, or all rows of a partition. You can express the size of the window as a range of data values offset from the value in the current row \(RANGE\), or the number of physical rows offset from the current row \(ROWS\).

When using the RANGE clause, you must also specify an ORDER BY clause because range calculations require values to be sorted. The ORDER BY clause for ranges must contain one expression, and that expression must result in either a date or a numeric value.

If you do not specify a ROWS or RANGE clause, the database server uses default window sizes based on whether an ORDER BY clause is present.


<dl>
<dt><b>

PRECEDING clause

</b></dt>
<dd>

Use the PRECEDING clause to define the first row of the window using the current row as a reference point. The starting row is expressed as the number of rows preceding the current row. For example, `5 PRECEDING` sets the window to start with the fifth row preceding the current row.

Use UNBOUNDED PRECEDING to set the first row in the window to be the first row in the partition.



</dd><dt><b>

BETWEEN clause

</b></dt>
<dd>

Use the BETWEEN clause to define the first and last row of the window, using the current row as a reference point. First and last rows are expressed as the number of rows preceding and following the current row, respectively. For example, `BETWEEN 3 PRECEDING AND 5 FOLLOWING` sets the window to start with the third row preceding the current row, and end with the fifth row following the current row.

Use BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING to set the first and last rows in the window to be the first and last row in the partition, respectively. This is equivalent to the default behavior if no ROW or RANGE clause is specified.



</dd><dt><b>

FOLLOWING clause

</b></dt>
<dd>

Use the FOLLOWING clause to define the last row of the window using the current row as a reference point. The last row is expressed as the number of rows following the current row.

Use UNBOUNDED FOLLOWING to set the last row in the window to be the last row in the partition.



</dd>
</dl>



</dd>
</dl>



<a name="loioc83b61b2b1814dbeaafa016b209a2d4d__section_htc_1fx_vbc"/>

## Remarks

The WINDOW clause must appear before the ORDER BY clause in a SELECT statement.

Except for the LIST function, all aggregate functions can be used as window functions. However, ranking aggregate functions \(RANK, DENSE\_RANK, PERCENT\_RANK, CUME\_DIST, and ROW\_NUMBER\) require an ORDER BY clause, and don’t allow a ROW or RANGE clause in the WINDOW clause or inline definition. For all other window functions, you can use any of the clauses.



<a name="loioc83b61b2b1814dbeaafa016b209a2d4d__section_s4q_pns_wbc"/>

## Privileges



### 


<dl>
<dt><b>

Connected to SAP HANA database as a SAP HANA database user.:

</b></dt>
<dd>

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the SAP HANA database REMOTE\_EXECUTE procedure associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).

-   See [REMOTE\_EXECUTE Guidance and Examples for Executing SQL Statements](remote-execute-guidance-and-examples-for-executing-sql-statements-fd99ac0.md).




</dd><dt><b>

Connected directly to data lake Relational Engine as a data lake Relational Engine user:

</b></dt>
<dd>

Beyond the privileges required by the SELECT statement, no additional privileges are required.



</dd>
</dl>



<a name="loioc83b61b2b1814dbeaafa016b209a2d4d__section_d4r_1fx_vbc"/>

## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

The WINDOW clause and window aggregate functions comprise optional SQL Language Features T611, "Elementary OLAP operations", and T612, "Advanced OLAP operations". The window functions FIRST\_VALUE and LAST\_VALUE aren’t in the standard.



</dd>
</dl>



<a name="loioc83b61b2b1814dbeaafa016b209a2d4d__section_cml_bfx_vbc"/>

## Examples

The following example returns an employee's salary and the average salary for all employees in the selected state. The results are ordered by state and then by surname.

```
SELECT EmployeeID, Surname, Salary, State,
  AVG( Salary ) OVER Salary_Window
FROM GROUPO.Employees
WINDOW Salary_Window AS ( PARTITION BY State )
ORDER BY State, Surname;
```

**Related Information**  


 <?sap-ot O2O class="- topic/link " href="a588f918af8b441a939c39e987597230.xml" text="WINDOW Clause for Data Lake Relational Engine" desc="" xtrc="link:1" xtrf="file:/home/builder/src/dita-all/vmv1718848528851/loioebf3112b870e474d9a791e9427bc62e1_en-US/src/content/localization/en-us/c83b61b2b1814dbeaafa016b209a2d4d.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> 

