<!-- loioa54d078b84f21015b96984e51c0cb74a -->

# DENSE\_RANK Function \[Analytical\] for Data Lake Relational Engine

Ranks items in a group.



```
DENSE_RANK () OVER ( ORDER BY <expression> [ ASC | DESC ] );
```



<a name="loioa54d078b84f21015b96984e51c0cb74a__DENSE_RANK_parm1"/>

## Parameters


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

A sort specification that can be any valid expression involving a column reference, aggregates, or expressions invoking these items.



</dd>
</dl>



<a name="loioa54d078b84f21015b96984e51c0cb74a__DENSE_RANK_returns1"/>

## Result Set

INTEGER



<a name="loioa54d078b84f21015b96984e51c0cb74a__DENSE_RANK_remarks1"/>

## Remarks

DENSE\_RANK is a rank analytical function. The dense rank of row R is defined as the number of rows preceding and including R that are distinct within the groups specified in the OVER clause or distinct over the entire result set. The difference between DENSE\_RANK and RANK is that DENSE\_RANK leaves no gap in the ranking sequence when there is a tie. RANK leaves a gap when there is a tie.

DENSE\_RANK requires an OVER \(ORDER BY\) clause. The ORDER BY clause specifies the parameter on which ranking is performed and the order in which the rows are sorted in each group. This ORDER BY clause is used only within the OVER clause and is not an ORDER BY for the SELECT. No aggregation functions in the rank query are allowed to specify DISTINCT.

The OVER clause indicates that the function operates on a query result set. The result set is the rows that are returned after the FROM, WHERE, GROUP BY, and HAVING clauses have all been evaluated. The OVER clause defines the data set of the rows to include in the computation of the rank analytical function.

The ASC or DESC parameter specifies the ordering sequence ascending or descending. Ascending order is the default.

DENSE\_RANK is allowed only in the select list of a SELECT or INSERT statement or in the ORDER BY clause of the SELECT statement. DENSE\_RANK can be in a view or a union. The DENSE\_RANK function cannot be used in a subquery, a HAVING clause, or in the select list of an UPDATE or DELETE statement. Only one rank analytical function is allowed per query.



<a name="loioa54d078b84f21015b96984e51c0cb74a__DENSE_RANK_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa54d078b84f21015b96984e51c0cb74a__DENSE_RANK_examples1"/>

## Example

The following statement illustrates the use of the DENSE\_RANK function:

```
SELECT s_suppkey, DENSE_RANK()
OVER ( ORDER BY ( SUM(s_acctBal) DESC )
AS rank_dense FROM supplier GROUP BY s_suppkey;

s_suppkey        sum_acctBal       rank_dense
supplier#011     200,000            1
supplier#002     200,000            1
supplier#013     123,000            2
supplier#004     110,000            3
supplier#035     110,000            3
supplier#006     50,000             4
supplier#021     10,000             5
```

**Related Information**  


[RANK Function \[Analytical\] for Data Lake Relational Engine](rank-function-analytical-for-data-lake-relational-engine-a57337e.md "Ranks items in a group.")

[DENSE_RANK Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/f68bfad26916474fba05b8e4555bf58e.html "Ranks items in a group.") :arrow_upper_right:

