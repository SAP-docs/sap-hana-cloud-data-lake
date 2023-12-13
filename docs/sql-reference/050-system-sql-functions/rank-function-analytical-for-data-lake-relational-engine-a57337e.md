<!-- loioa57337e084f21015aa46b31299b91d70 -->

# RANK Function \[Analytical\] for Data Lake Relational Engine

Ranks items in a group.



```
RANK () OVER ( [ PARTITION BY ] ORDER BY <expression> [ ASC | DESC ] );
```



<a name="loioa57337e084f21015aa46b31299b91d70__RANK_parm1"/>

## Parameters


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

A sort specification that can be any valid expression involving a column reference, aggregates, or expressions invoking these items.



</dd>
</dl>



<a name="loioa57337e084f21015aa46b31299b91d70__RANK_return1"/>

## Result Set

INTEGER



<a name="loioa57337e084f21015aa46b31299b91d70__RANK_remarks1"/>

## Remarks

`RANK` is a rank analytical function. The rank of row R is defined as the number of rows that precede R and are not peers of R. If two or more rows are not distinct within the groups specified in the `OVER` clause or distinct over the entire result set, then there are one or more gaps in the sequential rank numbering. The difference between `RANK` and `DENSE_RANK` is that `DENSE_RANK` leaves no gap in the ranking sequence when there is a tie. `RANK` leaves a gap when there is a tie.

`RANK` requires an `OVER (ORDER BY)` clause. The `ORDER BY` clause specifies the parameter on which ranking is performed and the order in which the rows are sorted in each group. This `ORDER BY` clause is used only within the `OVER` clause and is not an `ORDER BY` for the `SELECT`. No aggregation functions in the rank query are allowed to specify DISTINCT.

The `PARTITION BY` window partitioning clause in the `OVER (ORDER BY)` clause is optional.

The ASC or DESC parameter specifies the ordering sequence ascending or descending. Ascending order is the default.

The `OVER` clause indicates that the function operates on a query result set. The result set is the rows that are returned after the `FROM`, `WHERE`, `GROUP BY`, and `HAVING` clauses have all been evaluated. The `OVER` clause defines the data set of the rows to include in the computation of the rank analytical function.

`RANK` is allowed only in the select list of a `SELECT` or `INSERT` statement or in the `ORDER BY` clause of the `SELECT` statement. `RANK` can be in a view or a union. The `RANK` function cannot be used in a subquery, a `HAVING` clause, or in the select list of an `UPDATE` or `DELETE` statement. Only one rank analytical function is allowed per query.



<a name="loioa57337e084f21015aa46b31299b91d70__RANK_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise or SAP SQL Anywhere



<a name="loioa57337e084f21015aa46b31299b91d70__RANK_example1"/>

## Example

This statement illustrates the use of the `RANK` function:

```
SELECT Surname, Sex, Salary, RANK() OVER (PARTITION BY Sex 
ORDER BY Salary DESC) AS RANK FROM Employees 
WHERE State IN ('CA', 'AZ') AND DepartmentID IN (200, 300)
ORDER BY Sex, Salary DESC;
```

The results from the above query:

```
Surname           Sex      Salary     RANK
-------           ---      ------     ----
Savarino           F        72300.000  1
Jordan             F        51432.000  2
Clark              F        45000.000  3
Coleman            M        42300.000  1
Overbey            M        39300.000  2
```

**Related Information**  


[DENSE\_RANK Function \[Analytical\] for Data Lake Relational Engine](dense-rank-function-analytical-for-data-lake-relational-engine-a54d078.md "Ranks items in a group.")

[RANK Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/36d411cb841f42c792858d7cab19b626.html "Ranks items in a group.") :arrow_upper_right:

