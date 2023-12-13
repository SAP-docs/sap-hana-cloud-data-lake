<!-- loiofc8f0fd4618e4a47b712f7cc235fe437 -->

# PERCENT\_RANK Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Computes the \(fractional\) position of one row returned from a query with respect to the other rows returned by the query, as defined by the `ORDER BY` clause.



```
PERCENT_RANK () OVER ( ORDER BY <expression> [ ASC | DESC ] );
```



<a name="loiofc8f0fd4618e4a47b712f7cc235fe437__section_c22_kln_vrb"/>

## Parameters


<dl>
<dt><b>

OVER \(ORDER BY\)

</b></dt>
<dd>

The `ORDER BY` clause specifies the parameter on which ranking is performed and the order in which the rows are sorted in each group.



</dd><dt><b>

*<expression\>*

</b></dt>
<dd>

A sort specification that can be any valid expression involving a column reference, aggregates, or expressions invoking these items.



</dd><dt><b>

ASC | DESC

</b></dt>
<dd>

The ASC or DESC parameter specifies the ordering sequence ascending or descending. Ascending order is the default.



</dd>
</dl>



<a name="loiofc8f0fd4618e4a47b712f7cc235fe437__section_z2t_kln_vrb"/>

## Result Set

The `PERCENT_RANK` function returns a DOUBLE value between 0 and 1.

Returns a decimal value between 0 and 1.



<a name="loiofc8f0fd4618e4a47b712f7cc235fe437__section_d2d_lln_vrb"/>

## Remarks

`PERCENT_RANK` is a rank analytical function. The percent rank of a row R is defined as the rank of a row in the groups specified in the `OVER` clause minus one divided by the number of total rows in the groups specified in the `OVER` clause minus one. `PERCENT_RANK` returns a value between 0 and 1. The first row has a percent rank of zero.

The `PERCENT_RANK` of a row is calculated as follows, where *<Rx\>* is the rank position of a row in the group and *<NtotalRow\>* is the total number of rows in the group specified by the `OVER` clause:

```
(Rx - 1) / (NtotalRow - 1);
```

`PERCENT_RANK` requires an `OVER (ORDER BY)` clause. The `ORDER BY` clause specifies the parameter on which ranking is performed and the order in which the rows are sorted in each group. This `ORDER BY` clause is used only within the `OVER` clause and is not an `ORDER BY` for the `SELECT`. No aggregation functions in the rank query are allowed to specify `DISTINCT`.

The `OVER` clause indicates that the function operates on a query result set. The result set is the rows that are returned after the `FROM`, `WHERE`, `GROUP BY`, and `HAVING` clauses have all been evaluated. The `OVER` clause defines the data set of the rows to include in the computation of the rank analytical function.

`PERCENT_RANK` is allowed only in the select list of a `SELECT` or `INSERT` statement or in the `ORDER BY` clause of the `SELECT` statement. `PERCENT_RANK` can be in a view or a union. The `PERCENT_RANK` function cannot be used in a subquery, a `HAVING`clause, or in the select list of an `UPDATE` or `DELETE` statement. Only one rank analytical function is allowed per query.



<a name="loiofc8f0fd4618e4a47b712f7cc235fe437__section_xhr_lln_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise or SAP SQL Anywhere



<a name="loiofc8f0fd4618e4a47b712f7cc235fe437__section_tjg_mln_vrb"/>

## Example

The following statement illustrates the use of the `PERCENT_RANK` function:

```
SELECT s_suppkey, SUM(s_acctBal) AS sum_acctBal,
PERCENT_RANK() OVER ( ORDER BY SUM(s_acctBal) DESC )
AS percent_rank_all FROM supplier GROUP BY s_suppkey;

s_suppkey        sum_acctBal       percent_rank_all
supplier#011     200000            0
supplier#002     200000            0
supplier#013     123000            0.3333
supplier#004     110000            0.5
supplier#035     110000            0.5
supplier#006     50000             0.8333
supplier#021     10000             1
```

**Related Information**  


[PERCENT_RANK Function \[Analytical\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a56d183584f21015881bb3f46bb765ee.html "Computes the (fractional) position of one row returned from a query with respect to the other rows returned by the query, as defined by the ORDER BY clause.") :arrow_upper_right:

