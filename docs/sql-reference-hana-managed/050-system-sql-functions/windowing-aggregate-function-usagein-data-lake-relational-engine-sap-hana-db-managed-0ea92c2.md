<!-- loio0ea92c2f642240d5839f445ca482f41d -->

# Windowing Aggregate Function Usagein Data Lake Relational Engine \(SAP HANA DB-Managed\)

A major feature of the ISO/ANSI SQL extensions for OLAP is a construct called a window.

This windowing extension let users divide result sets of a query \(or a logical partition of a query\) into groups of rows called partitions and determine subsets of rows to aggregate with respect to the current row.

You can use three classes of window functions with a window: ranking functions, the row numbering function, and window aggregate functions.

Windowing extensions specify a window function type over a window name or specification and are applied to partitioned result sets within the scope of a single query expression.

Windowing operations let you establish information such as the ranking of each row within its partition, the distribution of values in rows within a partition, and similar operations. Windowing also lets you compute moving averages and sums on your data, enhancing the ability to evaluate your data and its impact on your operations.

A window partition is a subset of rows returned by a query, as defined by one or more columns in a special `OVER()` clause:

```
OVER (PARTITION BY <col1>, <col2>...);
```

**Related Information**  


[CORR Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](corr-function-for-data-lake-relational-engine-sap-hana-db-managed-ea68d7a.md "Returns the correlation coefficient of a set of number pairs.")

[COUNT Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](count-function-for-data-lake-relational-engine-sap-hana-db-managed-bd71ba2.md "Counts the number of rows in a group, depending on the specified parameters.")

[EXP\_WEIGHTED\_AVG Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](exp-weighted-avg-function-for-data-lake-relational-engine-sap-hana-db-managed-ac831a0.md "Calculates an exponential weighted moving average. Weightings determine the relative importance of each quantity that makes up the average.")

[FIRST\_VALUE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](first-value-function-for-data-lake-relational-engine-sap-hana-db-managed-9994e0a.md "Returns the first value from a set of values.")

[GROUPING Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](grouping-function-for-data-lake-relational-engine-sap-hana-db-managed-259511a.md "Identifies whether a column in a ROLLUP or CUBE operation result set is NULL because it is part of a subtotal row, or NULL because of the underlying data.")

[LAST\_VALUE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](last-value-function-for-data-lake-relational-engine-sap-hana-db-managed-8cf5191.md "Returns the last value from a set of values.")

[MAX Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](max-function-for-data-lake-relational-engine-sap-hana-db-managed-ae1f29e.md "Returns the maximum expression value found in each group of rows.")

[MEDIAN Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](median-function-for-data-lake-relational-engine-sap-hana-db-managed-d48698c.md "Returns the median of an expression.")

[MIN Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](min-function-for-data-lake-relational-engine-sap-hana-db-managed-6cfcb76.md "Returns the minimum expression value found in each group of rows.")

[REGR\_SXX Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](regr-sxx-function-for-data-lake-relational-engine-sap-hana-db-managed-9bf778d.md "Computes the slope of the linear regression line, fitted to non-NULL pairs.")

[REGR\_SXY Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](regr-sxy-function-for-data-lake-relational-engine-sap-hana-db-managed-1af7648.md "Returns the sum of products of the dependent and independent variables. Use REGR_SXY to evaluate the statistical validity of a regression model.")

[REGR\_SYY Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](regr-syy-function-for-data-lake-relational-engine-sap-hana-db-managed-e582164.md "Returns values that can evaluate the statistical validity of a regression model.")

[STDDEV Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](stddev-function-for-data-lake-relational-engine-sap-hana-db-managed-0dde65a.md "Returns the standard deviation of a set of numbers.")

[STDDEV\_POP Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](stddev-pop-function-for-data-lake-relational-engine-sap-hana-db-managed-b943ce2.md "Computes the standard deviation of a population consisting of a numeric-expression, as a DOUBLE.")

[STDDEV\_SAMP Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](stddev-samp-function-for-data-lake-relational-engine-sap-hana-db-managed-ae8f4df.md "Computes the standard deviation of a sample consisting of a numeric-expression, as a DOUBLE.")

[SUM Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](sum-function-for-data-lake-relational-engine-sap-hana-db-managed-d656f22.md "Returns the total of the specified expression for each group of rows.")

[VAR\_POP Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](var-pop-function-for-data-lake-relational-engine-sap-hana-db-managed-eb8e5a4.md "Computes the statistical variance of a population consisting of a numeric-expression, as a DOUBLE.")

[VAR\_SAMP Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](var-samp-function-for-data-lake-relational-engine-sap-hana-db-managed-4e77eae.md "Computes the statistical variance of a sample consisting of a numeric-expression, as a DOUBLE.")

[VARIANCE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](variance-function-for-data-lake-relational-engine-sap-hana-db-managed-974f709.md "Returns the variance of a set of numbers.")

[WEIGHTED\_AVG Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](weighted-avg-function-for-data-lake-relational-engine-sap-hana-db-managed-7a370d0.md "Calculates an arithmetically (or linearly) weighted average.")

