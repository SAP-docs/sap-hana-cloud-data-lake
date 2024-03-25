<!-- loiobebc33271f5545ff9e6a7fe0bb25b608 -->

# PERCENTILE\_DISC Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Given a percentile, returns the value that corresponds to that percentile. Assumes a discrete distribution data model.



> ### Note:  
> If you are simply trying to compute a percentile, use the `NTILE` function instead, with a value of 100.



```
PERCENTILE_DISC ( <expression1> )
WITHIN GROUP ( ORDER BY <expression2> [ ASC | DESC ] );
```



<a name="loiobebc33271f5545ff9e6a7fe0bb25b608__section_lz1_nkn_vrb"/>

## Parameters


<dl>
<dt><b>

*<expression1\>*

</b></dt>
<dd>

A constant of numeric data type and range from 0 to 1 \(inclusive\). If the argument is NULL, then a “wrong argument for percentile” error is returned. If the argument value is less than 0 or greater than 1, then a “data value out of range” error is returned.



</dd><dt><b>

*<expression2\>*

</b></dt>
<dd>

A sort specification that must be a single expression involving a column reference. Multiple expressions are not allowed and no rank analytical functions, set functions, or subqueries are allowed in this sort expression.



</dd>
</dl>



<a name="loiobebc33271f5545ff9e6a7fe0bb25b608__section_b1y_nkn_vrb"/>

## Remarks

The inverse distribution analytical functions return a k-th percentile value, which can be used to help establish a threshold acceptance value for a set of data. The function `PERCENTILE_DISC` takes a percentile value as the function argument and operates on a group of data specified in the `WITHIN GROUP` clause or operates on the entire data set. The function returns one value per group. If the `GROUP BY` column from the query is not present, the result is a single row. The data type of the results is the same as the data type of its `ORDER BY` item specified in the `WITHIN GROUP` clause. `PERCENTILE_DISC` supports all data types that can be sorted in data lake Relational Engine.

`PERCENTILE_DISC` requires a `WITHIN GROUP (ORDER BY)` clause.

The `ORDER BY` clause, which must be present, specifies the expression on which the percentile function is performed and the order in which the rows are sorted in each group. This `ORDER BY` clause is used only within the `WITHIN GROUP` clause and is not an `ORDER BY` for the `SELECT`.

The `WITHIN GROUP` clause distributes the query result into an ordered data set from which the function calculates a result. The `WITHIN GROUP` clause must contain a single sort item. If the `WITHIN GROUP` clause contains more or less than one sort item, an error is reported.

The ASC or DESC parameter specifies the ordering sequence ascending or descending. Ascending order is the default.

The `PERCENTILE_DISC` function is allowed in a subquery, a `HAVING` clause, a view, or a union. `PERCENTILE_DISC` can be used anywhere the simple nonanalytical aggregate functions are used. The `PERCENTILE_DISC` function ignores the NULL value in the data set.



<a name="loiobebc33271f5545ff9e6a7fe0bb25b608__section_pyr_4kn_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise or SAP SQL Anywhere



<a name="loiobebc33271f5545ff9e6a7fe0bb25b608__section_u12_pkn_vrb"/>

## Example

The following example uses the `PERCENTILE_DISC` function to determine the 10th percentile value for car sales in a region.

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

The following `SELECT` statement contains the `PERCENTILE_DISC` function:

```
SELECT region, PERCENTILE_DISC(0.1)
WITHIN GROUP ( ORDER BY sales DESC )
FROM carSales GROUP BY region;
```

The result of the `SELECT` statement lists the 10th percentile value for car sales in a region:

```
region           percentile_cont
Northeast        900
Northwest        800
South            500
```

**Related Information**  


[PERCENTILE_DISC Function \[Analytical\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a56e219484f21015b3a4f46749d3faf5.html "Given a percentile, returns the value that corresponds to that percentile. Assumes a discrete distribution data model.") :arrow_upper_right:

