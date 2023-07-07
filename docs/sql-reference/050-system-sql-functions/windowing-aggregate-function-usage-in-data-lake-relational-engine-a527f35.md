<!-- loioa527f35684f21015a092a69470690c91 -->

# Windowing Aggregate Function Usage in Data Lake Relational Engine

A major feature of the ISO/ANSI SQL extensions for OLAP is a construct called a window.

This windowing extension let users divide result sets of a query \(or a logical partition of a query\) into groups of rows called partitions and determine subsets of rows to aggregate with respect to the current row.

You can use three classes of window functions with a window: ranking functions, the row numbering function, and window aggregate functions.

Windowing extensions specify a window function type over a window name or specification and are applied to partitioned result sets within the scope of a single query expression.

Windowing operations let you establish information such as the ranking of each row within its partition, the distribution of values in rows within a partition, and similar operations. Windowing also lets you compute moving averages and sums on your data, enhancing the ability to evaluate your data and its impact on your operations.

A window partition is a subset of rows returned by a query, as defined by one or more columns in a special `OVER()` clause:

```
OVER (PARTITION BY <col1>, <col2>...)
```

**Related Information**  


[Function Support of Large Object Data](https://help.sap.com/viewer/a8937bea84f21015a80bc776cf758d50/2023_2_QRC/en-US/a60363a384f21015a7f7bc6286516522.html "Learn about the functions that support the LONG BINARY and LONG VARCHAR data types.") :arrow_upper_right:

[CORR Function \[Aggregate\] for Data Lake Relational Engine](corr-function-aggregate-for-data-lake-relational-engine-a53fefe.md "Returns the correlation coefficient of a set of number pairs.")

[COUNT Function \[Aggregate\] for Data Lake Relational Engine](count-function-aggregate-for-data-lake-relational-engine-a54290f.md "Counts the number of rows in a group, depending on the specified parameters.")

[EXP\_WEIGHTED\_AVG Function \[Aggregate\] for Data Lake Relational Engine](exp-weighted-avg-function-aggregate-for-data-lake-relational-engine-a551b4f.md "Calculates an exponential weighted moving average. Weightings determine the relative importance of each quantity that makes up the average.")

[FIRST\_VALUE Function \[Aggregate\] for Data Lake Relational Engine](first-value-function-aggregate-for-data-lake-relational-engine-a5523f3.md "Returns the first value from a set of values.")

[GROUPING Function \[Aggregate\] for Data Lake Relational Engine](grouping-function-aggregate-for-data-lake-relational-engine-a554461.md "Identifies whether a column in a ROLLUP or CUBE operation result set is NULL because it is part of a subtotal row, or NULL because of the underlying data.")

[LAST\_VALUE Function \[Aggregate\] for Data Lake Relational Engine](last-value-function-aggregate-for-data-lake-relational-engine-a55bfa7.md "Returns the last value from a set of values.")

[MAX Function \[Aggregate\] for Data Lake Relational Engine](max-function-aggregate-for-data-lake-relational-engine-a5626d6.md "Returns the maximum expression value found in each group of rows.")

[MEDIAN Function \[Aggregate\] for Data Lake Relational Engine](median-function-aggregate-for-data-lake-relational-engine-a562edf.md "Returns the median of an expression.")

[MIN Function \[Aggregate\] for Data Lake Relational Engine](min-function-aggregate-for-data-lake-relational-engine-a5638af.md "Returns the minimum expression value found in each group of rows.")

[REGR\_AVGX Function \[Aggregate\] for Data Lake Relational Engine](regr-avgx-function-aggregate-for-data-lake-relational-engine-a573b70.md "Computes the average of the independent variable of the regression line.")

[REGR\_COUNT Function \[Aggregate\] for Data Lake Relational Engine](regr-count-function-aggregate-for-data-lake-relational-engine-a574c56.md "Returns an integer that represents the number of non-NULL number pairs used to fit the regression line.")

[REGR\_INTERCEPT Function \[Aggregate\] for Data Lake Relational Engine](regr-intercept-function-aggregate-for-data-lake-relational-engine-a57548b.md "Computes the y-intercept of the linear regression line that best fits the dependent and independent variables.")

[REGR\_R2 Function \[Aggregate\] for Data Lake Relational Engine](regr-r2-function-aggregate-for-data-lake-relational-engine-a575c77.md "Computes the coefficient of determination (also referred to as R-squared or the goodness-of-fit statistic) for the regression line.")

[REGR\_SLOPE Function \[Aggregate\] for Data Lake Relational Engine](regr-slope-function-aggregate-for-data-lake-relational-engine-a57647a.md "Computes the slope of the linear regression line, fitted to non-NULL pairs.")

[REGR\_SXX Function \[Aggregate\] for Data Lake Relational Engine](regr-sxx-function-aggregate-for-data-lake-relational-engine-a576c83.md "Computes the slope of the linear regression line, fitted to non-NULL pairs.")

[REGR\_SXY Function \[Aggregate\] for Data Lake Relational Engine](regr-sxy-function-aggregate-for-data-lake-relational-engine-a57748f.md "Returns the sum of products of the dependent and independent variables. Use REGR_SXY to evaluate the statistical validity of a regression model.")

[REGR\_SYY Function \[Aggregate\] for Data Lake Relational Engine](regr-syy-function-aggregate-for-data-lake-relational-engine-a57806c.md "Returns values that can evaluate the statistical validity of a regression model.")

[STDDEV Function \[Aggregate\] for Data Lake Relational Engine](stddev-function-aggregate-for-data-lake-relational-engine-a583716.md "Returns the standard deviation of a set of numbers.")

[STDDEV\_POP Function \[Aggregate\] for Data Lake Relational Engine](stddev-pop-function-aggregate-for-data-lake-relational-engine-a583f35.md "Computes the standard deviation of a population consisting of a numeric-expression, as a DOUBLE.")

[STDDEV\_SAMP Function \[Aggregate\] for Data Lake Relational Engine](stddev-samp-function-aggregate-for-data-lake-relational-engine-a584728.md "Computes the standard deviation of a sample consisting of a numeric-expression, as a DOUBLE.")

[SUM Function \[Aggregate\] for Data Lake Relational Engine](sum-function-aggregate-for-data-lake-relational-engine-a5889fe.md "Returns the total of the specified expression for each group of rows.")

[VAR\_POP Function \[Aggregate\] for Data Lake Relational Engine](var-pop-function-aggregate-for-data-lake-relational-engine-a58ec03.md "Computes the statistical variance of a population consisting of a numeric-expression, as a DOUBLE.")

[VAR\_SAMP Function \[Aggregate\] for Data Lake Relational Engine](var-samp-function-aggregate-for-data-lake-relational-engine-a58f41a.md "Computes the statistical variance of a sample consisting of a numeric-expression, as a DOUBLE.")

[VARIANCE Function \[Aggregate\] for Data Lake Relational Engine](variance-function-aggregate-for-data-lake-relational-engine-a58fdc8.md "Returns the variance of a set of numbers.")

[WEIGHTED\_AVG Function \[Aggregate\] for Data Lake Relational Engine](weighted-avg-function-aggregate-for-data-lake-relational-engine-a590e30.md "Calculates an arithmetically (or linearly) weighted average.")

