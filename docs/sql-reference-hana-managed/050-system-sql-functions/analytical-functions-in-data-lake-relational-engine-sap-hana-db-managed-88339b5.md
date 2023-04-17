<!-- loio88339b5651e64ffabe7457d74956c77d -->

# Analytical Functions in Data Lake Relational Engine \(SAP HANA DB-Managed\)

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

-   [CUME\_DIST Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](cume-dist-function-for-data-lake-relational-engine-sap-hana-db-managed-6572908.md)
-   [DENSE\_RANK Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](dense-rank-function-for-data-lake-relational-engine-sap-hana-db-managed-f68bfad.md)
-   [LAG Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](lag-function-for-data-lake-relational-engine-sap-hana-db-managed-0561e54.md)
-   [LEAD Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](lead-function-for-data-lake-relational-engine-sap-hana-db-managed-b6a23b0.md)
-   [NTILE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](ntile-function-for-data-lake-relational-engine-sap-hana-db-managed-97741f1.md)
-   [PERCENT\_RANK Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](percent-rank-function-for-data-lake-relational-engine-sap-hana-db-managed-fc8f0fd.md)
-   [PERCENTILE\_CONT Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](percentile-cont-function-for-data-lake-relational-engine-sap-hana-db-managed-126ea72.md)
-   [PERCENTILE\_DISC Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](percentile-disc-function-for-data-lake-relational-engine-sap-hana-db-managed-bebc332.md)
-   [RANK Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](rank-function-for-data-lake-relational-engine-sap-hana-db-managed-36d411c.md)
-   [ROW\_NUMBER Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](row-number-function-for-data-lake-relational-engine-sap-hana-db-managed-2ebca29.md)

**Related Information**  


[Aggregate Functions in Data Lake Relational Engine \(SAP HANA DB-Managed\)](aggregate-functions-in-data-lake-relational-engine-sap-hana-db-managed-d84cfa4.md "Aggregate functions summarize data over a group of rows from the database. The groups are formed using the GROUP BY clause of the SELECT statement.")

[AVG Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](avg-function-for-data-lake-relational-engine-sap-hana-db-managed-cfa9951.md "Computes the average of a numeric expression for a set of rows, or computes the average of a set of unique values.")

[COUNT Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](count-function-for-data-lake-relational-engine-sap-hana-db-managed-bd71ba2.md "Counts the number of rows in a group, depending on the specified parameters.")

[GROUPING Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](grouping-function-for-data-lake-relational-engine-sap-hana-db-managed-259511a.md "Identifies whether a column in a ROLLUP or CUBE operation result set is NULL because it is part of a subtotal row, or NULL because of the underlying data.")

[MAX Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](max-function-for-data-lake-relational-engine-sap-hana-db-managed-ae1f29e.md "Returns the maximum expression value found in each group of rows.")

[MIN Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](min-function-for-data-lake-relational-engine-sap-hana-db-managed-6cfcb76.md "Returns the minimum expression value found in each group of rows.")

[STDDEV Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](stddev-function-for-data-lake-relational-engine-sap-hana-db-managed-0dde65a.md "Returns the standard deviation of a set of numbers.")

[STDDEV\_POP Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](stddev-pop-function-for-data-lake-relational-engine-sap-hana-db-managed-b943ce2.md "Computes the standard deviation of a population consisting of a numeric-expression, as a DOUBLE.")

[STDDEV\_SAMP Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](stddev-samp-function-for-data-lake-relational-engine-sap-hana-db-managed-ae8f4df.md "Computes the standard deviation of a sample consisting of a numeric-expression, as a DOUBLE.")

[SUM Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](sum-function-for-data-lake-relational-engine-sap-hana-db-managed-d656f22.md "Returns the total of the specified expression for each group of rows.")

[VAR\_POP Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](var-pop-function-for-data-lake-relational-engine-sap-hana-db-managed-eb8e5a4.md "Computes the statistical variance of a population consisting of a numeric-expression, as a DOUBLE.")

[VAR\_SAMP Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](var-samp-function-for-data-lake-relational-engine-sap-hana-db-managed-4e77eae.md "Computes the statistical variance of a sample consisting of a numeric-expression, as a DOUBLE.")

[VARIANCE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](variance-function-for-data-lake-relational-engine-sap-hana-db-managed-974f709.md "Returns the variance of a set of numbers.")

