<!-- loioa57c3ea884f21015b4f8c850a5a5357f -->

# ROW\_NUMBER Function \[Analytical\] for Data Lake Relational Engine

A ranking function that returns a unique row number for each row in a window partition, restarting the row numbering at the start of every window partition.



```
ROW_NUMBER() OVER ( [ PARTITION BY <window partition> ] ORDER BY <window ordering> )
```



<a name="loioa57c3ea884f21015b4f8c850a5a5357f__ROW_NUMBER_parm1"/>

## Parameters


<dl>
<dt><b>

*<window partition\>*

</b></dt>
<dd>

\(Optional\) One or more value expressions separated by commas indicating how you want to divide the set of result rows.



</dd><dt><b>

*<window ordering\>*

</b></dt>
<dd>

Defines the expressions for sorting rows within window partitions, if specified, or within the result set if you did not specify a window partition.



</dd>
</dl>



<a name="loioa57c3ea884f21015b4f8c850a5a5357f__ROW_NUMBER_remarks1"/>

## Remarks

If no window partitions exist, the function numbers the rows in the result set from 1 to the cardinality of the table.

The `ROW_NUMBER` function requires an `OVER` \(`ORDER_BY`\) window specification. The window partitioning clause in the `OVER` \(`ORDER_BY`\) clause is optional. The `OVER` \(`ORDER_BY`\) clause must not contain a window frame `ROWS`/`RANGE` specification.



<a name="loioa57c3ea884f21015b4f8c850a5a5357f__ROW_NUMBER_standards1"/>

## Standards and Compatibility

SQL – ISO/ANSI SQL compliant. SQL/OLAP feature T611.



<a name="loioa57c3ea884f21015b4f8c850a5a5357f__ROW_NUMBER_example1"/>

## Example

The following example returns salary data from the Employees table, partitions the result set by department ID, and orders the data according to employee start date. The `ROW_NUMBER` function assigns each row a row number, and restarts the row numbering for each window partition:

```
SELECT DepartmentID dID, StartDate, Salary, ROW_NUMBER()OVER(PARTITION 
BY dID ORDER BY StartDate) FROM  Employees ORDER BY 1,2;
```

The returned result set is:

```
dID        StartDate    Salary      Row_number()
=========  ===========  ==========  =============
100         1986-10-14  42,998.000     1
100         1987-07-23  39,875.500     2
100         1988-03-23  37,400.000     3
100         1989-04-20  42,500.000     4
100         1990-01-15  42,100.000     5
200         1985-02-03  38,500.000     1
200         1987-02-19  39,300.000     2
200         1988-11-22  39,800.000     3
200         1989-06-01  34,892.000     4
200         1990-05-13  33,890.000     5
200         1990-07-11  37,803.000     6
```

**Related Information**  


[ROW_NUMBER Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/2ebca29e7b31469497df90d36ea7422e.html "A ranking function that returns a unique row number for each row in a window partition, restarting the row numbering at the start of every window partition.") :arrow_upper_right:

