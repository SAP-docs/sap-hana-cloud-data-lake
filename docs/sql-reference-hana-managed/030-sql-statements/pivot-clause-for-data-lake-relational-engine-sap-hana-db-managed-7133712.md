<!-- loio71337123850742e79ab57ded4fdef45f -->

# PIVOT Clause for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Pivots a table expression in the FROM clause of a SELECT statement \(FROM *<pivoted-derived-table\>*\) into a pivoted derived table. Pivoted derived tables offer an easy way to rotate row values from a column in a table expression into multiple columns, and perform aggregation where needed on the columns included in the result set.



```
FROM <pivoted-derived-table>
```

```
<pivoted-derived-table> :
<pivot-source-table> PIVOT  ( <pivot-clause> ) [ AS ] <pivoted-correlation-name>
```

```
<pivot-source-table> : <table-expression>
```

```
<pivot-clause> : 
   <aggregate-clause> <pivot-for-clause> <pivot-in-clause>
```

```
<aggregate-clause> :
<aggregate-function> ( [ <aggregate-expression> ] ) [ [ AS ] <aggregate-alias> ] [,...]
```

```
<pivot-for-clause> : 
FOR <pivot-column>
| FOR ( <pivot-column> [,...] )
```

```
<pivot-in-clause> : 
IN ( <constant-expression> [ [ AS ] <constant-expression-alias> ] [,...] )
| IN ( ( <constant-expression> [,...] ) [ [ AS ] <constant-expression-alias> ] [,...] )
```



<a name="loio71337123850742e79ab57ded4fdef45f__section_kpt_ljp_njb"/>

## Parameters


<dl class="glossary">
<dt><b>

*<aggregate-function\>* \( \[ *<aggregate-expression\>* \] \) \[ \[ AS \] *<aggregate-alias\>* \]

</b></dt>
<dd>

Specify any aggregate function that returns a single value for a set of rows.

-   *<aggregate-function\>* – specify any aggregate function that returns a single value for a set of rows \(also known as a scalar function\).

-   *<aggregate-expression\>* – specify the parameters of the aggregate function. The aggregate expression must reference only columns found in *<pivot-source-table\>*.

-   *<aggregate-alias\>* – specify an alias for the aggregate function. The list of aggregate functions can have at most one aggregate function without an alias. Aggregate aliases, together with the IN clause aliases, are used to generate the names of the new columns of the pivoted derived table. As a best practice, always specify an alias for your aggregate.




</dd><dt><b>

FOR clause

</b></dt>
<dd>

Specify one or more columns on which to pivot the data. *<pivot-column\>* must be a column in *<pivot-source-table\>*. If you specify more than one *<pivot-column\>*, then you must enclose them in parentheses.



</dd><dt><b>

IN \( *<constant-expression\>* \[\[ AS \] *<constant-expression-alias\>* \] \[,...\] \)

</b></dt>
<dd>

Specify a set of constant expressions on which to pivot the data. Use this syntax when the FOR clause lists only one column, namely, FOR *<pivot-column\>*.

If an alias is not specified, then the implicit alias is the string representing the constant expression. For example, the implicit alias for the constant 10 is "10." Always specify an alias for *<constant-expression\>*. Use implicit and explicit aliases for constant expressions in the IN clause, together with aggregate aliases, to generate the names of the new columns of the pivoted derived table.

Each new column in the pivoted derived table corresponds to a pairing of an aggregate function and an IN item, and has a name that reflects the pairing. The first part of the name is the alias of the IN item, and the second part of the name \(after the underscore\) is the alias of the aggregate function. If a generated column name is an invalid identifier, then an error is generated and the statement fails.



</dd><dt><b>

IN \( \( *<constant-expression\>* \[,...\] \) \[ \[ AS \] *<constant-expression-alias\>* \] \[,...\] \)

</b></dt>
<dd>

Specify a set of lists containing constant expressions on which to pivot the data. Use this form of the IN clause when you specify multiple columns in the FOR clause. The number of columns specified in the FOR clause must be equal to the number of items in any constant list of the IN clause.

If an alias is not specified, then the implicit alias is the string representing the list of constant expressions. For example, the implicit alias for the constant list \(10, 20\) is "\(10, 20\)". Implicit and explicit aliases for constant expressions in the IN clause, together with the aggregate aliases, are used to generate the names of the new columns of the pivoted derived table.



</dd>
</dl>



<a name="loio71337123850742e79ab57ded4fdef45f__section_lpt_ljp_njb"/>

## Remarks

The definition of a pivoted derived table contains an input table expression, *<pivot-source-table\>*. The columns and values to pivot on are defined in the FOR and IN clauses. The grouping columns of the pivoted derived tables are a subset of the columns of *<pivot-source-table\>*. A pivoted derived table is computed by grouping *<pivot-source-table\>* on the grouping columns and then computing the aggregate functions specified in the aggregate clause. The pivoted derived table has a column for each value of the grouping columns. There are extra columns added to the pivoted derived table, one for each pair of an item in the aggregate clause and an item in the IN clause. The values of the new columns are the aggregate functions specified in the aggregate clause. The names of these new columns are generated from the aliases specified in the aggregate clause for aggregate functions, and the aliases and values specified in the IN clause. In total, if *<A\>* aggregate functions are specified, and the IN clause has *<I\>* elements, then there are *<A\>* x *<I\>* extra columns.



<a name="loio71337123850742e79ab57ded4fdef45f__section_npt_ljp_njb"/>

## Side Effects

None.



<a name="loio71337123850742e79ab57ded4fdef45f__section_opt_ljp_njb"/>

## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Not in the standard.



</dd>
</dl>



The following example selects data from the Employees table and pivots it on the DepartmentID column, where the Department ID is 100, 200, 300, 400, or 500.

```
SELECT * 
FROM ( SELECT DepartmentID, State, Salary 
       FROM   Employees
       WHERE State IN ( 'OR', 'CA', 'AZ', 'UT' )
     ) MyPivotSourceData
   PIVOT ( 
      SUM( Salary ) TotalSalary  
      FOR DepartmentID IN ( 100, 200, 300, 400, 500 )
   ) MyPivotedData
ORDER BY State;
```


<table>
<tr>
<th valign="top">

STATE



</th>
<th valign="top">

100\_TotalSalary



</th>
<th valign="top">

200\_TotalSalary



</th>
<th valign="top">

300\_TotalSalary



</th>
<th valign="top">

400\_TotalSalary



</th>
<th valign="top">

500\_TotalSalary



</th>
</tr>
<tr>
<td valign="top">

AZ



</td>
<td valign="top">

\(NULL\)



</td>
<td valign="top">

\(NULL\)



</td>
<td valign="top">

93,732.000



</td>
<td valign="top">

\(NULL\)



</td>
<td valign="top">

85,300.800



</td>
</tr>
<tr>
<td valign="top">

CA



</td>
<td valign="top">

\(NULL\)



</td>
<td valign="top">

156,600.000



</td>
<td valign="top">

\(NULL\)



</td>
<td valign="top">

\(NULL\)



</td>
<td valign="top">

\(NULL\)



</td>
</tr>
<tr>
<td valign="top">

OR



</td>
<td valign="top">

\(NULL\)



</td>
<td valign="top">

47,653.000



</td>
<td valign="top">

\(NULL\)



</td>
<td valign="top">

80,339.000



</td>
<td valign="top">

54,790.000



</td>
</tr>
<tr>
<td valign="top">

UT



</td>
<td valign="top">

306,318.690



</td>
<td valign="top">

37,900.000



</td>
<td valign="top">

31,200.000



</td>
<td valign="top">

107,129.000



</td>
<td valign="top">

59,479.000



</td>
</tr>
</table>

In the results, the aggregate alias and the values for DepartmentID are included in the column names of the result set \(for example, 100\_TotalSalary\) to clarify which value is being pivoted. The column names in this example mean "the total salary for department X". The salaries for employees in each State/DepartmentID tuple are aggregated \(in this case, summed together\).

