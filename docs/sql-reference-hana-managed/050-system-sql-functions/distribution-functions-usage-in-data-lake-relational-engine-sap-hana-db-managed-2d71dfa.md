<!-- loio2d71dfa1838944d3a0af3f338f06b4cf -->

# Distribution Functions Usage in Data Lake Relational Engine \(SAP HANA DB-Managed\)

The inverse distribution analytical functions PERCENTILE\_CONT and PERCENTILE\_DISC take a percentile value as the function argument and operate on a group of data specified in the WITHIN GROUP clause, or operate on the entire data set.



These functions return one value per group. For PERCENTILE\_DISC, the data type of the results is the same as the data type of its ORDER BY item specified in the WITHIN GROUP clause. For PERCENTILE\_CONT, the data type of the results is either numeric, if the ORDER BY item in the WITHIN GROUP clause is a numeric, or double, if the ORDER BY item is an integer or floating-point.

The inverse distribution analytical functions require a `WITHIN GROUP (ORDER BY)` clause. For example:

```
PERCENTILE_CONT ( <expression1> ) WITHIN GROUP ( ORDER BY <expression2> [ASC | DESC ] );
```

The value of *<expression1\>* must be a constant of numeric data type and range from 0 to 1 \(inclusive\). If the argument is NULL, then a "wrong argument for percentile" error is returned. If the argument value is less than 0, or greater than 1, then a "data value out of range" error is returned.

The ORDER BY clause, which must be present, specifies the expression on which the percentile function is performed and the order in which the rows are sorted in each group. This ORDER BY clause is used only within the WITHIN GROUP clause and is not an ORDER BY for the SELECT.

The WITHIN GROUP clause distributes the query result into an ordered data set from which the function calculates a result.

The value *<expression2\>* is a sort specification that must be a single expression involving a column reference. Multiple expressions are not allowed and no rank analytical functions, set functions, or subqueries are allowed in this sort expression.

The ASC or DESC parameter specifies the ordering sequence as ascending or descending. Ascending order is the default.

Inverse distribution analytical functions are allowed in a subquery, a HAVING clause, a view, or a union. The inverse distribution functions can be used anywhere the simple non analytical aggregate functions are used. The inverse distribution functions ignore the NULL value in the data set.

**Related Information**  


[PERCENTILE\_CONT Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](percentile-cont-function-for-data-lake-relational-engine-sap-hana-db-managed-126ea72.md "Given a percentile, returns the value that corresponds to that percentile. Assumes a continuous distribution data model.")

[PERCENTILE\_DISC Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](percentile-disc-function-for-data-lake-relational-engine-sap-hana-db-managed-bebc332.md "Given a percentile, returns the value that corresponds to that percentile. Assumes a discrete distribution data model.")

