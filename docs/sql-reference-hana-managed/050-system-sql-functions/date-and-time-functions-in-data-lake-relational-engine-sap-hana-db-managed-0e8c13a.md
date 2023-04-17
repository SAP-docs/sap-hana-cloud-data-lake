<!-- loio0e8c13a7e76e44bebe44138dde7efd77 -->

# Date and Time Functions in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Date and time functions perform conversion, extraction, or manipulation operations on date and time data types and can return date and time information.



The date and time functions allow manipulation of time units. Most time units \(such as MONTH\) have four functions for time manipulation, although only two names are used \(such as MONTH and MONTHS\).

These functions are Transact-SQL date and time functions. They allow an alternative way of accessing and manipulating date and time functions:

-   DATEADD
-   DATEDIFF
-   DATENAME
-   DATEPART
-   GETDATE

You should convert arguments to date functions to dates before using them. For example:

-   Incorrect: `DAYS ( '1995-11-17', 2 )`
-   Correct: `DAYS ( date( '1995-11-17' ), 2 )`

Data lake Relational Engine does not have the same constants or data type promotions as SAP SQL Anywhere, with which it shares a common user interface. If you issue a SELECT statement without a FROM clause, the statement is passed to SAP SQL Anywhere. The following statement is handled exclusively by SAP SQL Anywhere:

```
SELECT WEEKS('1998/11/01');
```

The following statement, processed by data lake Relational Engine, uses a different starting point for the WEEKS function and returns a different result than the statement above:

```
SELECT WEEKS('1998/11/01') FROM iq_dummy;
```

Consider another example. The `MONTHS` function returns the number of months since an “arbitrary starting date.” The “arbitrary starting date” of data lake Relational Engine, the imaginary date 0000-01-01, is chosen to produce the most efficient date calculations and is consistent across various data parts. SAP SQL Anywhere uses the starting date 0000/02/29. The first statement below, processed by SAP SQL Anywhere, returns the answer 12, and the second, by data lake Relational Engine, returns the answer 11:

```
SELECT MONTHS('0001/01/01');
```

```
SELECT MONTHS('0001/01/01') FROM iq_dummy;
```

However, also consider these statements:

```
SELECT DAYS('0001/01/01');
```

```
SELECT DAYS('0001/01/01') FROM iq_dummy;
```

The first, processed by SAP SQL Anywhere, yields the value 307 \(from this calculation: 366-31-28 \(the number of days in year 0 - a leap year - 366, less the number of days before 0000/02/29 \(31 + 28\), but the second, processed by data lake Relational Engine, yields 366.

For the most consistent results, therefore, always include the table name in the `FROM` clause whether you need it or not.

> ### Note:  
> Create a dummy table with only one column and row. You can then reference this table in the `FROM` clause for any `SELECT` statement that uses date or time functions, thus ensuring processing by data lake Relational Engine, and consistent results.



The following functions are available:

-   [DATE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](date-function-for-data-lake-relational-engine-sap-hana-db-managed-e5839f4.md)
-   [DATEADD Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](dateadd-function-for-data-lake-relational-engine-sap-hana-db-managed-2020154.md)
-   [DATECEILING Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](dateceiling-function-for-data-lake-relational-engine-sap-hana-db-managed-faa4713.md)
-   [DATEDIFF Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](datediff-function-for-data-lake-relational-engine-sap-hana-db-managed-7bf7fa8.md)
-   [DATEFLOOR Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](datefloor-function-for-data-lake-relational-engine-sap-hana-db-managed-907ca83.md)
-   [DATEFORMAT Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](dateformat-function-for-data-lake-relational-engine-sap-hana-db-managed-d8071cc.md)
-   [DATENAME Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](datename-function-for-data-lake-relational-engine-sap-hana-db-managed-b6977f3.md)
-   [DATEPART Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](datepart-function-for-data-lake-relational-engine-sap-hana-db-managed-a07008d.md)
-   [DATEROUND Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](dateround-function-for-data-lake-relational-engine-sap-hana-db-managed-0e97cec.md)
-   [DATETIME Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](datetime-function-for-data-lake-relational-engine-sap-hana-db-managed-87c2ebf.md)
-   [DAY Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](day-function-for-data-lake-relational-engine-sap-hana-db-managed-ff00ee7.md)
-   [DAYNAME Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](dayname-function-for-data-lake-relational-engine-sap-hana-db-managed-be690a0.md)
-   [DAYS Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](days-function-for-data-lake-relational-engine-sap-hana-db-managed-80456cf.md)
-   [DOW Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](dow-function-for-data-lake-relational-engine-sap-hana-db-managed-aae6da5.md)
-   [EXTRACT Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](extract-function-for-data-lake-relational-engine-sap-hana-db-managed-5abf140.md)
-   [GETDATE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](getdate-function-for-data-lake-relational-engine-sap-hana-db-managed-a9570ce.md)
-   [HOUR Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](hour-function-for-data-lake-relational-engine-sap-hana-db-managed-13ca8f8.md)
-   [HOURS Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](hours-function-for-data-lake-relational-engine-sap-hana-db-managed-21c2140.md)
-   [ISDATE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](isdate-function-for-data-lake-relational-engine-sap-hana-db-managed-f28668e.md)
-   [MINUTE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](minute-function-for-data-lake-relational-engine-sap-hana-db-managed-4b1c8e2.md)
-   [MINUTES Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](minutes-function-for-data-lake-relational-engine-sap-hana-db-managed-488cdf4.md)
-   [MONTH Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](month-function-for-data-lake-relational-engine-sap-hana-db-managed-63319cc.md)
-   [MONTHNAME Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](monthname-function-for-data-lake-relational-engine-sap-hana-db-managed-2a2b0c1.md)
-   [MONTHS Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](months-function-for-data-lake-relational-engine-sap-hana-db-managed-8c326df.md)
-   [NOW Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](now-function-for-data-lake-relational-engine-sap-hana-db-managed-b711c80.md)
-   [QUARTER Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](quarter-function-for-data-lake-relational-engine-sap-hana-db-managed-57330a5.md)
-   [QUARTERSTR Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](quarterstr-function-for-data-lake-relational-engine-sap-hana-db-managed-b6d0dea.md)
-   [SECOND Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](second-function-for-data-lake-relational-engine-sap-hana-db-managed-ff2ca42.md)
-   [SECONDS Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](seconds-function-for-data-lake-relational-engine-sap-hana-db-managed-18801f8.md)
-   [TODAY Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](today-function-for-data-lake-relational-engine-sap-hana-db-managed-1f01004.md)
-   [TOLOCALTIME Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](tolocaltime-function-for-data-lake-relational-engine-sap-hana-db-managed-9533cea.md)
-   [WEEKS Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](weeks-function-for-data-lake-relational-engine-sap-hana-db-managed-1bad0c4.md)
-   [YEAR Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](year-function-for-data-lake-relational-engine-sap-hana-db-managed-54d4912.md)
-   [YEARS Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](years-function-for-data-lake-relational-engine-sap-hana-db-managed-1d6751f.md)
-   [YMD Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](ymd-function-for-data-lake-relational-engine-sap-hana-db-managed-0cf8ed2.md)

