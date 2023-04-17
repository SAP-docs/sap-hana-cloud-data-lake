<!-- loio126ea72fa1b94e76828493c4602e8942 -->

# PERCENTILE\_CONT Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Given a percentile, returns the value that corresponds to that percentile. Assumes a continuous distribution data model.



> ### Note:  
> If you are simply trying to compute a percentile, use the `NTILE` function instead, with a value of 100.



```
PERCENTILE_CONT ( <expression1> )
WITHIN GROUP ( ORDER BY <expression2> [ ASC | DESC ] )
```



<a name="loio126ea72fa1b94e76828493c4602e8942__section_h1g_zkn_vrb"/>

## Parameters

 *<expression1\>*
 :   A constant of numeric data type and range from 0 to 1 \(inclusive\). If the argument is NULL, a “wrong argument for percentile” error is returned. If the argument value is less than 0 or greater than 1, a “data value out of range” error is returned

  *<expression2\>*
 :   A sort specification that must be a single expression involving a column reference. Multiple expressions are not allowed and no rank analytical functions, set functions, or subqueries are allowed in this sort expression.

 

<a name="loio126ea72fa1b94e76828493c4602e8942__section_rqp_zkn_vrb"/>

## Remarks

The inverse distribution analytical functions return a k-th percentile value, which can be used to help establish a threshold acceptance value for a set of data. The function `PERCENTILE_CONT` takes a percentile value as the function argument, and operates on a group of data specified in the `WITHIN GROUP` clause, or operates on the entire data set. The function returns one value per group. If the `GROUP BY` column from the query is not present, the result is a single row. The data type of the results is the same as the data type of its `ORDER BY` item specified in the `WITHIN GROUP` clause. The data type of the `ORDER BY` expression for `PERCENTILE_CONT` must be numeric.

`PERCENTILE_CONT` requires a `WITHIN GROUP (ORDER BY)` clause.

The `ORDER BY` clause, which must be present, specifies the expression on which the percentile function is performed and the order in which the rows are sorted in each group. For the `PERCENTILE_CONT` function, the data type of this expression must be numeric. This `ORDER BY` clause is used only within the `WITHIN GROUP` clause and is not an `ORDER BY` for the `SELECT`.

The `WITHIN GROUP` clause distributes the query result into an ordered data set from which the function calculates a result. The `WITHIN GROUP` clause must contain a single sort item. If the `WITHIN GROUP` clause contains more or less than one sort item, an error is reported.

The ASC or DESC parameter specifies the ordering sequence ascending or descending. Ascending order is the default.

The `PERCENTILE_CONT` function is allowed in a subquery, a `HAVING` clause, a view, or a union. `PERCENTILE_CONT` can be used anywhere the simple non-analytical aggregate functions are used. The `PERCENTILE_CONT` function ignores the NULL value in the data set.



<a name="loio126ea72fa1b94e76828493c4602e8942__section_shj_1ln_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise or SAP SQL Anywhere



<a name="loio126ea72fa1b94e76828493c4602e8942__section_fx5_1ln_vrb"/>

## Example

The following example uses the `PERCENTILE_CONT` function to determine the 10th percentile value for car sales in a region.

The example uses the following data set:

```
sales       region        dealer_name
900         Northeast     Boston
800         Northeast     Worcester
800         Northeast     Providence
700         Northeast     Lowell
540         Northeast     Natick
500         Northeast     New Haven
450         Northeast     Hartford
800         Northwest     SF
600         Northwest     Seattle
500         Northwest     Portland
400         Northwest     Dublin
500         South         Houston
400         South         Austin
300         South         Dallas
200         South         Dover
```

The following `SELECT` statement contains the `PERCENTILE_CONT` function:

```
SELECT region, PERCENTILE_CONT(0.1)
WITHIN GROUP ( ORDER BY sales DESC )
FROM carSales GROUP BY region;
```

The result of the `SELECT` statement lists the 10th percentile value for car sales in a region:

```
region           percentile_cont
Northeast        840
Northwest        740
South            470
```

**Related Information**  


[PERCENTILE_CONT Function [Analytical] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a56d9fa784f21015b6c8d94588153331.html "Given a percentile, returns the value that corresponds to that percentile. Assumes a continuous distribution data model.") :arrow_upper_right:

