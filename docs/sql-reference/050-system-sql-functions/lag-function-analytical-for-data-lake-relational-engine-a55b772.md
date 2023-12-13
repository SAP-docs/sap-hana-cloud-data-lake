<!-- loioa55b772a84f2101583fef0038bcd8bb0 -->

# LAG Function \[Analytical\] for Data Lake Relational Engine

An interrow function that returns the value of an attribute in a previous row in the table or table partition.



```
LAG ( <value_expr> [, <offset> [, <default> ] ] ) 
    OVER ( [ PARTITION BY <window_partition> ] ORDER BY <window_ordering> );
```



<a name="loioa55b772a84f2101583fef0038bcd8bb0__LAG_parm1"/>

## Parameters


<dl>
<dt><b>

*<value\_expr\>*

</b></dt>
<dd>

Table column or expression defining the offset data to return from the table.



</dd><dt><b>

*<offset\>*

</b></dt>
<dd>

The number of rows above the current row, expressed as a non-negative exact numeric literal, or as a SQL variable with exact numeric data. The permitted range is 0 to 231.



</dd><dt><b>

*<default\>*

</b></dt>
<dd>

The value to return if the *<offset\>* value goes beyond the scope of the cardinality of the table or partition.



</dd><dt><b>

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



<a name="loioa55b772a84f2101583fef0038bcd8bb0__LAG_remarks1"/>

## Remarks

The LAG function requires an OVER \(ORDER\_BY\) window specification. The window partitioning clause in the OVER \(ORDER\_BY\) clause is optional. The OVER \(ORDER\_BY\) clause must not contain a window frame ROWS/RANGE specification.

You cannot define an analytic expression in *<value\_expr\>*. That is, you cannot nest analytic functions, but you can use other built-in function expressions for *<value\_expr\>*.

You must enter a non-negative numeric data type for *<offset\>*. Entering 0 returns the current row. Entering a negative number generates an error.

The default value of *<default\>* is NULL. The data type of *<default\>* must be implicitly convertible to the data type of the *<value\_expr\>* value or else data lake Relational Engine generates a conversion error.



<a name="loioa55b772a84f2101583fef0038bcd8bb0__LAG_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa55b772a84f2101583fef0038bcd8bb0__LAG_eample1"/>

## Example

The following example returns salary data from the Employees table, partitions the data by department ID, and orders the data according to employee start date. The LAG function returns the salary from the previous row \(a physical offset of one row\) and displays it under the LAG \(Salary\) column:

```
SELECT DepartmentID dID, StartDate, Salary, LAG(Salary, 1) 
    OVER (PARTITION BY dID ORDER BY StartDate) FROM Employees ORDER BY 1,2;
```

The returned result set is:

```
dID        StartDate    Salary      Lag(Salary)
=========  ===========  ==========  =============
100        1984-08-28   45,700.000  NULL
100        1985-01-01   62,000.000  45,700.000
100        1985-06-17   57,490.000  62,000.000
100        1986-06-07   72,995.000  57,490.000
100        1986-07-01   48,023.690  72,995.000
...
200        1985-02-03   38,500.000  NULL
200        1985-12-06   54,800.000  38,500.000
200        1987-02-19   39,300.000  54,800.000
200        1987-07-10   49,500.000  39,300.000
200        1988-10-04   54,600.000  49,500.000
200        1988-11-12   39,800.000  54,600.000 
...
```

**Related Information**  


[LEAD Function \[Analytical\] for Data Lake Relational Engine](lead-function-analytical-for-data-lake-relational-engine-a55d051.md "An interrow function that returns the value of an attribute in a subsequent row in the table or table partition.")

[LAG Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/0561e5415d37410b837052f20b4239b9.html "An interrow function that returns the value of an attribute in a previous row in the table or table partition.") :arrow_upper_right:

