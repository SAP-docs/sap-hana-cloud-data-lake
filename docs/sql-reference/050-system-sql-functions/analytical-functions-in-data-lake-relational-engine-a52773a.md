<!-- loioa52773a684f21015b3c4b84e700f7a66 -->

# Analytical Functions in Data Lake Relational Engine

Analytical functions include simple aggregates, window functions, and numeric functions.



-   Simple aggregates – AVG, COUNT, MAX, MIN, and SUM, STDDEV, and VARIANCE

    > ### Note:  
    > You can use all simple aggregates, except the Grouping\(\) function, with an OLAP windowed function.

-   Window functions:
    -   Windowing aggregates – AVG, COUNT, MAX, MIN, and SUM.
    -   Ranking functions – RANK, DENSE\_RANK, PERCENT\_RANK, ROW\_NUMBER, and NTILE.
    -   Statistical functions – STDDEV, STDDEV\_SAMP, STDDEV\_POP, VARIANCE, VAR\_SAMP, and VAR\_POP.
    -   Distribution functions – PERCENTILE\_CONT and PERCENTILE\_DISC.
    -   Interrow functions – LAG and LEAD.

-   Numeric functions – WIDTH\_BUCKET, CEIL, and LN, EXP, POWER, SQRT, and FLOOR.

Unlike some aggregate functions, you cannot specify DISTINCT in window functions.



\* The OLAP SQL standard allows Grouping\(\) in GROUP BY CUBE, or GROUP BY ROLLUP operations only.



The following functions are available:

-   [CUME\_DIST Function \[Analytical\] for Data Lake Relational Engine](cume-dist-function-analytical-for-data-lake-relational-engine-a54314b.md)
-   [DENSE\_RANK Function \[Analytical\] for Data Lake Relational Engine](dense-rank-function-analytical-for-data-lake-relational-engine-a54d078.md)
-   [LAG Function \[Analytical\] for Data Lake Relational Engine](lag-function-analytical-for-data-lake-relational-engine-a55b772.md)
-   [LEAD Function \[Analytical\] for Data Lake Relational Engine](lead-function-analytical-for-data-lake-relational-engine-a55d051.md)
-   [NTILE Function \[Analytical\] for Data Lake Relational Engine](ntile-function-analytical-for-data-lake-relational-engine-a5695f3.md)
-   [PERCENT\_RANK Function \[Analytical\] for Data Lake Relational Engine](percent-rank-function-analytical-for-data-lake-relational-engine-a56d183.md)
-   [PERCENTILE\_CONT Function \[Analytical\] for Data Lake Relational Engine](percentile-cont-function-analytical-for-data-lake-relational-engine-a56d9fa.md)
-   [PERCENTILE\_DISC Function \[Analytical\] for Data Lake Relational Engine](percentile-disc-function-analytical-for-data-lake-relational-engine-a56e219.md)
-   [RANK Function \[Analytical\] for Data Lake Relational Engine](rank-function-analytical-for-data-lake-relational-engine-a57337e.md)
-   [ROW\_NUMBER Function \[Analytical\] for Data Lake Relational Engine](row-number-function-analytical-for-data-lake-relational-engine-a57c3ea.md)

**Related Information**  


[Aggregate Functions in Data Lake Relational Engine](aggregate-functions-in-data-lake-relational-engine-a526f10.md "Aggregate functions summarize data over a group of rows from the database. The groups are formed using the GROUP BY clause of the SELECT statement.")

[AVG Function \[Aggregate\] for Data Lake Relational Engine](avg-function-aggregate-for-data-lake-relational-engine-a535f04.md "Computes the average of a numeric expression for a set of rows, or computes the average of a set of unique values.")

[COUNT Function \[Aggregate\] for Data Lake Relational Engine](count-function-aggregate-for-data-lake-relational-engine-a54290f.md "Counts the number of rows in a group, depending on the specified parameters.")

[GROUPING Function \[Aggregate\] for Data Lake Relational Engine](grouping-function-aggregate-for-data-lake-relational-engine-a554461.md "Identifies whether a column in a ROLLUP or CUBE operation result set is NULL because it is part of a subtotal row, or NULL because of the underlying data.")

[MAX Function \[Aggregate\] for Data Lake Relational Engine](max-function-aggregate-for-data-lake-relational-engine-a5626d6.md "Returns the maximum expression value found in each group of rows.")

[MIN Function \[Aggregate\] for Data Lake Relational Engine](min-function-aggregate-for-data-lake-relational-engine-a5638af.md "Returns the minimum expression value found in each group of rows.")

[STDDEV Function \[Aggregate\] for Data Lake Relational Engine](stddev-function-aggregate-for-data-lake-relational-engine-a583716.md "Returns the standard deviation of a set of numbers.")

[STDDEV\_POP Function \[Aggregate\] for Data Lake Relational Engine](stddev-pop-function-aggregate-for-data-lake-relational-engine-a583f35.md "Computes the standard deviation of a population consisting of a numeric-expression, as a DOUBLE.")

[STDDEV\_SAMP Function \[Aggregate\] for Data Lake Relational Engine](stddev-samp-function-aggregate-for-data-lake-relational-engine-a584728.md "Computes the standard deviation of a sample consisting of a numeric-expression, as a DOUBLE.")

[SUM Function \[Aggregate\] for Data Lake Relational Engine](sum-function-aggregate-for-data-lake-relational-engine-a5889fe.md "Returns the total of the specified expression for each group of rows.")

[VAR\_POP Function \[Aggregate\] for Data Lake Relational Engine](var-pop-function-aggregate-for-data-lake-relational-engine-a58ec03.md "Computes the statistical variance of a population consisting of a numeric-expression, as a DOUBLE.")

[VAR\_SAMP Function \[Aggregate\] for Data Lake Relational Engine](var-samp-function-aggregate-for-data-lake-relational-engine-a58f41a.md "Computes the statistical variance of a sample consisting of a numeric-expression, as a DOUBLE.")

[VARIANCE Function \[Aggregate\] for Data Lake Relational Engine](variance-function-aggregate-for-data-lake-relational-engine-a58fdc8.md "Returns the variance of a set of numbers.")

