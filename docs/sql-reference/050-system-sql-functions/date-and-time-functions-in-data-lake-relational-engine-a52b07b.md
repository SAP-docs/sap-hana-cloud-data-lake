<!-- loioa52b07be84f21015baa5a63dd21b850b -->

# Date and Time Functions in Data Lake Relational Engine

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

-   [DATE Function \[Date and Time\] for Data Lake Relational Engine](date-function-date-and-time-for-data-lake-relational-engine-a544131.md)
-   [DATEADD Function \[Date and Time\] for Data Lake Relational Engine](dateadd-function-date-and-time-for-data-lake-relational-engine-a5449de.md)
-   [DATECEILING Function \[Date and Time\] for Data Lake Relational Engine](dateceiling-function-date-and-time-for-data-lake-relational-engine-a545210.md)
-   [DATEDIFF Function \[Date and Time\] for Data Lake Relational Engine](datediff-function-date-and-time-for-data-lake-relational-engine-a545a63.md)
-   [DATEFLOOR Function \[Date and Time\] for Data Lake Relational Engine](datefloor-function-date-and-time-for-data-lake-relational-engine-a5462b6.md)
-   [DATEFORMAT Function \[Date and Time\] for Data Lake Relational Engine](dateformat-function-date-and-time-for-data-lake-relational-engine-a546abe.md)
-   [DATENAME Function \[Date and Time\] for Data Lake Relational Engine](datename-function-date-and-time-for-data-lake-relational-engine-a5472b7.md)
-   [DATEPART Function \[Date and Time\] for Data Lake Relational Engine](datepart-function-date-and-time-for-data-lake-relational-engine-a547b06.md)
-   [DATEROUND Function \[Date and Time\] for Data Lake Relational Engine](dateround-function-date-and-time-for-data-lake-relational-engine-a5483a3.md)
-   [DATETIME Function \[Date and Time\] for Data Lake Relational Engine](datetime-function-date-and-time-for-data-lake-relational-engine-a548c21.md)
-   [DAY Function \[Date and Time\] for Data Lake Relational Engine](day-function-date-and-time-for-data-lake-relational-engine-a5493fe.md)
-   [DAYNAME Function \[Date and Time\] for Data Lake Relational Engine](dayname-function-date-and-time-for-data-lake-relational-engine-a549c43.md)
-   [DAYS Function \[Date and Time\] for Data Lake Relational Engine](days-function-date-and-time-for-data-lake-relational-engine-a54a45b.md)
-   [DOW Function \[Date and Time\] for Data Lake Relational Engine](dow-function-date-and-time-for-data-lake-relational-engine-a54e817.md)
-   [EXTRACT Function \[Date and Time\] for Data Lake Relational Engine](extract-function-date-and-time-for-data-lake-relational-engine-c3565b1.md)
-   [GETDATE Function \[Date and Time\] for Data Lake Relational Engine](getdate-function-date-and-time-for-data-lake-relational-engine-a553449.md)
-   [HOUR Function \[Date and Time\] for Data Lake Relational Engine](hour-function-date-and-time-for-data-lake-relational-engine-a55651a.md)
-   [HOURS Function \[Date and Time\] for Data Lake Relational Engine](hours-function-date-and-time-for-data-lake-relational-engine-a556e14.md)
-   [ISDATE Function \[Date and Time\] for Data Lake Relational Engine](isdate-function-date-and-time-for-data-lake-relational-engine-a559f0f.md)
-   [MINUTE Function \[Date and Time\] for Data Lake Relational Engine](minute-function-date-and-time-for-data-lake-relational-engine-a5640f2.md)
-   [MINUTES Function \[Date and Time\] for Data Lake Relational Engine](minutes-function-date-and-time-for-data-lake-relational-engine-a5648d4.md)
-   [MONTH Function \[Date and Time\] for Data Lake Relational Engine](month-function-date-and-time-for-data-lake-relational-engine-a565928.md)
-   [MONTHNAME Function \[Date and Time\] for Data Lake Relational Engine](monthname-function-date-and-time-for-data-lake-relational-engine-a566193.md)
-   [MONTHS Function \[Date and Time\] for Data Lake Relational Engine](months-function-date-and-time-for-data-lake-relational-engine-a566ced.md)
-   [NOW Function \[Date and Time\] for Data Lake Relational Engine](now-function-date-and-time-for-data-lake-relational-engine-a568dfd.md)
-   [QUARTER Function \[Date and Time\] for Data Lake Relational Engine](quarter-function-date-and-time-for-data-lake-relational-engine-a571b27.md)
-   [QUARTERSTR Function \[Date and Time\] for Data Lake Relational Engine](quarterstr-function-date-and-time-for-data-lake-relational-engine-8fbd6b7.md)
-   [SECOND Function \[Date and Time\] for Data Lake Relational Engine](second-function-date-and-time-for-data-lake-relational-engine-a57dc03.md)
-   [SECONDS Function \[Date and Time\] for Data Lake Relational Engine](seconds-function-date-and-time-for-data-lake-relational-engine-a57e4e7.md)
-   [TODAY Function \[Date and Time\] for Data Lake Relational Engine](today-function-date-and-time-for-data-lake-relational-engine-a58aae9.md)
-   [TOLOCALTIME Function \[Date and Time\] for Data Lake Relational Engine](tolocaltime-function-date-and-time-for-data-lake-relational-engine-b472502.md)
-   [WEEKS Function \[Date and Time\] for Data Lake Relational Engine](weeks-function-date-and-time-for-data-lake-relational-engine-a590601.md)
-   [YEAR Function \[Date and Time\] for Data Lake Relational Engine](year-function-date-and-time-for-data-lake-relational-engine-a591eb9.md)
-   [YEARS Function \[Date and Time\] for Data Lake Relational Engine](years-function-date-and-time-for-data-lake-relational-engine-a5926bf.md)
-   [YMD Function \[Date and Time\] for Data Lake Relational Engine](ymd-function-date-and-time-for-data-lake-relational-engine-a592fc9.md)

