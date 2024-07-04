<!-- loiob6a23b08149640eab401cd98acf6b638 -->

# LEAD Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

An interrow function that returns the value of an attribute in a subsequent row in the table or table partition.



```
LEAD ( <value_expr>[, <offset>[, <default> ] ] ) 
    OVER ( [ PARTITION BY <window_partition> ] ORDER BY <window_ordering> );
```



<a name="loiob6a23b08149640eab401cd98acf6b638__section_bmd_kdh_trb"/>

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

The number of rows below the current row, expressed as a non-negative exact numeric literal, or as a SQL variable with exact numeric data. The permitted range is 0 to 231.



</dd><dt><b>

*<default\>*

</b></dt>
<dd>

The value to return if the *<offset\>* value goes beyond the scope of the table or partition.



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



<a name="loiob6a23b08149640eab401cd98acf6b638__section_zfs_kdh_trb"/>

## Remarks

The LEAD function requires an OVER \(ORDER\_BY\) window specification. The window partitioning clause in the OVER \(ORDER\_BY\) clause is optional. The OVER \(ORDER\_BY\) clause must not contain a window frame ROWS/RANGE specification.

You cannot define an analytic expression in *<value\_expr\>*. That is, you cannot nest analytic functions, but you can use other built-in function expressions for *<value\_expr\>*.

You must enter a non-negative numeric data type for *<offset\>*. Entering `0` returns the current row. Entering a negative number generates an error.

The default value of *<default\>* is NULL. The data type of *<default\>* must be implicitly convertible to the data type of the *<value\_expr\>* value or else data lake Relational Engine generates a conversion error.



<a name="loiob6a23b08149640eab401cd98acf6b638__section_yyk_ldh_trb"/>

## Standards and Compatibility

SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loiob6a23b08149640eab401cd98acf6b638__section_qbd_mdh_trb"/>

## Examples

The following example returns salary data from the Employees table, partitions the data by department ID, and orders the data according to employee start date. The LEAD function returns the salary from the next row \(a physical offset of one row\) and displays it under the LEAD \(Salary\) column:

```
SELECT DepartmentID dID, StartDate, Salary, LEAD(Salary, 1) 
    OVER (PARTITION BY dID ORDER BY StartDate) FROM  Employees ORDER BY 1,2;
```

The returned result set is:

```
dID        StartDate    Salary      Lead(Salary)
=========  ===========  ==========  =============
100        1984-08-28    45,700.000    62,000.000
100        1985-01-01    62,000.000    57,490.000
100        1985-06-17    57,490.000    72,995.000
100        1986-06-07    72,995.000    48,023.690
...
100        1990-08-19    54,900.000    NULL
200        1985-02-03    38,500.000    39,300.000
200        1987-02-19    39,300.000    49,500.000
200        1987-07-10    49,500.000    54,600.000
200        1988-11-28    46,200.000    34,892.000
200        1989-06-01    34,892.000    87,500.000
...
200        1993-08-12    47,653.000    NULL
```

**Related Information**  


[LEAD Function \[Analytical\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a55d051484f21015b82fe3d1795a7a94.html "An interrow function that returns the value of an attribute in a subsequent row in the table or table partition.") :arrow_upper_right:

