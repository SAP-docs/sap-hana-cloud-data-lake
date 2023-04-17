<!-- loio97741f155cc24e2ea035db70a29da3b0 -->

# NTILE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Distributes query results into a specified number of buckets and assigns the bucket number to each row in the bucket.



```
NTILE ( <expression1> )
OVER ( ORDER BY <expression2> [ ASC | DESC ] )
```



<a name="loio97741f155cc24e2ea035db70a29da3b0__section_eyy_nnn_vrb"/>

## Parameters

 *<expression1\>*
 :   A constant integer from 1 to 32767, which specifies the number of buckets.

  *<expression2\>*
 :   A sort specification that can be any valid expression involving a column reference, aggregates, or expressions invoking these items.

  ASC | DESC
 :   The ASC or DESC parameter specifies the ordering sequence ascending or descending. Ascending order is the default.

 

<a name="loio97741f155cc24e2ea035db70a29da3b0__section_c1p_4nn_vrb"/>

## Remarks

`NTILE` is a rank analytical function that distributes query results into a specified number of buckets and assigns the bucket number to each row in the bucket. You can divide a result set into one-hundredths \(percentiles\), tenths \(deciles\), fourths \(quartiles\), or other numbers of groupings.

`NTILE` requires an `OVER (ORDER BY)`clause. The `ORDER BY` clause specifies the parameter on which ranking is performed and the order in which the rows are sorted in each group. This `ORDER BY` clause is used only within the `OVER` clause and is not an `ORDER BY` for the `SELECT`. No aggregation functions in the rank query are allowed to specify `DISTINCT`.

The `OVER` clause indicates that the function operates on a query result set. The result set is the rows that are returned after the `FROM`, `WHERE`, `GROUP BY`, and `HAVING` clauses have all been evaluated. The `OVER` clause defines the data set of the rows to include in the computation of the rank analytical function.

`NTILE` is allowed only in the select list of a `SELECT` or `INSERT` statement or in the `ORDER BY` clause of the `SELECT` statement. `NTILE` can be in a view or a union. The `NTILE` function cannot be used in a subquery, a `HAVING` clause, or in the select list of an `UPDATE` or `DELETE` statement. Only one `NTILE` function is allowed per query.



<a name="loio97741f155cc24e2ea035db70a29da3b0__section_bfm_pnn_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise or SAP SQL Anywhere



<a name="loio97741f155cc24e2ea035db70a29da3b0__section_i42_qnn_vrb"/>

## Example

The following example uses the `NTILE` function to determine the sale status of car dealers. The dealers are divided into four groups based on the number of cars each dealer sold. The dealers with `ntile = 1` are in the top 25% for car sales:

```
SELECT dealer_name, sales,
NTILE(4) OVER ( ORDER BY sales DESC )
FROM carSales;


dealer_name        sales       ntile
Boston             1000        1
Worcester          950         1
Providence         950         1
SF                 940         1
Lowell             900         2
Seattle            900         2
Natick             870         2
New Haven          850         2
Portland           800         3
Houston            780         3
Hartford           780         3
Dublin             750         3
Austin             650         4
Dallas             640         4
Dover              600         4
```

To find the top 10% of car dealers by sales, you specify `NTILE(10)` in the example `SELECT` statement. Similarly, to find the top 50% of car dealers by sales, specify `NTILE(2)`.

**Related Information**  


[NTILE Function [Analytical] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a5695f3f84f21015a23ae9730b31eef2.html "Distributes query results into a specified number of buckets and assigns the bucket number to each row in the bucket.") :arrow_upper_right:

