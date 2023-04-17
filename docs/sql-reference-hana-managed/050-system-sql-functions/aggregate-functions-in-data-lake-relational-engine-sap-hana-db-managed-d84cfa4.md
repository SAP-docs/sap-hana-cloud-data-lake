<!-- loiod84cfa4d66c14a18b8e66d8338da81f5 -->

# Aggregate Functions in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Aggregate functions summarize data over a group of rows from the database. The groups are formed using the GROUP BY clause of the SELECT statement.



Simple aggregate functions, such as SUM\(\), MIN\(\), MAX\(\), AVG\(\) and COUNT\(\) are allowed only in the select list and in the HAVING and ORDER BY clauses of a SELECT statement. These functions summarize data over a group of rows from the database. Groups are formed using the GROUP BY clause of the SELECT statement.

A class of aggregate functions, called window functions, provides moving averages and cumulative measures that compute answers to queries such as, “What is the quarterly moving average of the Dow Jones Industrial average?” or “List all employees and their cumulative salaries for each department.”

-   Simple aggregate functions, such as AVG\(\), COUNT\(\), MAX\(\), MIN\(\), and SUM\(\) summarize data over a group of rows from the database. The groups are formed using the GROUP BY clause of the SELECT statement.

-   Newer statistical aggregate functions that take one argument include STDDEV\(\), STDDEV\_SAMP\(\), STDDEV\_POP\(\), VARIANCE\(\), VAR\_SAMP\(\), and VAR\_POP\(\).


Both the simple and newer categories of aggregates can be used as a windowing function that incorporates a window clause in a SQL query specification \(a window\) that conceptually creates a moving window over a result set as it is processed.

Another class of window aggregate functions supports analysis of time series data. Like the simple aggregate and statistical aggregate functions, you can use these window aggregates with a SQL query specification \(or *<window-spec\>*\). The time series window aggregate functions calculate correlation, linear regression, ranking, and weighted average results:

-   ISO/ANSI SQL:2008 OLAP functions for time series analysis include: CORR\(\), COVAR\_POP\(\), COVAR\_SAMP\(\), CUME\_DIST\(\), FIRST\_VALUE\(\), LAST\_VALUE\(\), REGR\_AVGX\(\), REGR\_AVGY\(\), REGR\_COUNT\(\), REGR\_INTERCEPT\(\), REGR\_R2\(\), REGR\_SLOPE\(\), REGR\_SXX\(\), REGR\_SXY\(\), and REGR\_SYY\(\).

-   Non-ISO/ANSI SQL:2008 OLAP aggregate function extensions used in the database industry include FIRST\_VALUE\(\), MEDIAN\(\), and LAST\_VALUE\(\).

-   Weighted OLAP aggregate functions that calculate weighted moving averages include EXP\_WEIGHTED\_AVG\(\) and WEIGHTED\_AVG\(\).


The aggregate functions AVG, SUM, STDDEV, and VARIANCE do not support the binary data types \(`BINARY` and `VARBINARY`\).



The following functions are available:

-   [AVG Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](avg-function-for-data-lake-relational-engine-sap-hana-db-managed-cfa9951.md)
-   [CORR Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](corr-function-for-data-lake-relational-engine-sap-hana-db-managed-ea68d7a.md)
-   [COVAR\_POP Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](covar-pop-function-for-data-lake-relational-engine-sap-hana-db-managed-6d40c83.md)
-   [COVAR\_SAMP Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](covar-samp-function-for-data-lake-relational-engine-sap-hana-db-managed-3a06491.md)
-   [COUNT Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](count-function-for-data-lake-relational-engine-sap-hana-db-managed-bd71ba2.md)
-   [EXP\_WEIGHTED\_AVG Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](exp-weighted-avg-function-for-data-lake-relational-engine-sap-hana-db-managed-ac831a0.md)
-   [FIRST\_VALUE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](first-value-function-for-data-lake-relational-engine-sap-hana-db-managed-9994e0a.md)
-   [GROUPING Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](grouping-function-for-data-lake-relational-engine-sap-hana-db-managed-259511a.md)
-   [LAST\_VALUE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](last-value-function-for-data-lake-relational-engine-sap-hana-db-managed-8cf5191.md)
-   [LIST Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](list-function-for-data-lake-relational-engine-sap-hana-db-managed-7b4801a.md)
-   [MAX Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](max-function-for-data-lake-relational-engine-sap-hana-db-managed-ae1f29e.md)
-   [MEDIAN Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](median-function-for-data-lake-relational-engine-sap-hana-db-managed-d48698c.md)
-   [MIN Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](min-function-for-data-lake-relational-engine-sap-hana-db-managed-6cfcb76.md)
-   [REGR\_AVGX Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](regr-avgx-function-for-data-lake-relational-engine-sap-hana-db-managed-af6ea13.md)
-   [REGR\_AVGY Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](regr-avgy-function-for-data-lake-relational-engine-sap-hana-db-managed-a54d2f0.md)
-   [REGR\_COUNT Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](regr-count-function-for-data-lake-relational-engine-sap-hana-db-managed-6ae6fc4.md)
-   [REGR\_INTERCEPT Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](regr-intercept-function-for-data-lake-relational-engine-sap-hana-db-managed-150d7d8.md)
-   [REGR\_R2 Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](regr-r2-function-for-data-lake-relational-engine-sap-hana-db-managed-e970c79.md)
-   [REGR\_SLOPE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](regr-slope-function-for-data-lake-relational-engine-sap-hana-db-managed-2b3cc76.md)
-   [REGR\_SXX Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](regr-sxx-function-for-data-lake-relational-engine-sap-hana-db-managed-9bf778d.md)
-   [REGR\_SXY Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](regr-sxy-function-for-data-lake-relational-engine-sap-hana-db-managed-1af7648.md)
-   [REGR\_SYY Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](regr-syy-function-for-data-lake-relational-engine-sap-hana-db-managed-e582164.md)
-   [STDDEV Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](stddev-function-for-data-lake-relational-engine-sap-hana-db-managed-0dde65a.md)
-   [STDDEV\_POP Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](stddev-pop-function-for-data-lake-relational-engine-sap-hana-db-managed-b943ce2.md)
-   [STDDEV\_SAMP Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](stddev-samp-function-for-data-lake-relational-engine-sap-hana-db-managed-ae8f4df.md)
-   [SUM Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](sum-function-for-data-lake-relational-engine-sap-hana-db-managed-d656f22.md)
-   [VAR\_POP Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](var-pop-function-for-data-lake-relational-engine-sap-hana-db-managed-eb8e5a4.md)
-   [VAR\_SAMP Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](var-samp-function-for-data-lake-relational-engine-sap-hana-db-managed-4e77eae.md)
-   [VARIANCE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](variance-function-for-data-lake-relational-engine-sap-hana-db-managed-974f709.md)
-   [WEIGHTED\_AVG Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](weighted-avg-function-for-data-lake-relational-engine-sap-hana-db-managed-7a370d0.md)

