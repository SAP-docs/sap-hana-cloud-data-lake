<!-- loioa545a63784f210158075c22cd6f85d3a -->

# DATEDIFF Function \[Date and Time\] for Data Lake Relational Engine

Returns the interval between two dates.



```
DATEDIFF ( <date-part>, <date-expression1>, <date-expression2> )
```



<a name="loioa545a63784f210158075c22cd6f85d3a__DATEDIFF_parm1"/>

## Parameters


<dl>
<dt><b>

*<date-part\>*

</b></dt>
<dd>

The date part in which the interval is to be measured.



</dd><dt><b>

*<date-expression1\>*

</b></dt>
<dd>

The starting date for the interval. This value is subtracted from *<date-expression2\>* to return the number of date parts between the two arguments.



</dd><dt><b>

*<date-expression2\>*

</b></dt>
<dd>

The ending date for the interval. *<date-expression1\>* is subtracted from this value to return the number of date parts between the two arguments.



</dd>
</dl>



<a name="loioa545a63784f210158075c22cd6f85d3a__DATEDIFF_returns1"/>

## Returns

INT



<a name="loioa545a63784f210158075c22cd6f85d3a__DATEDIFF_remarks1"/>

## Remarks

This function calculates the number of date parts between two specified dates. The result is a signed integer value equal to \(date2 - date1\), in date parts.

DATEDIFF results are truncated, not rounded, when the result is not an even multiple of the date part.

When you use day as the date part, DATEDIFF returns the number of midnights between the two times specified, including the second date, but not the first. For example, the following statement returns the value 5. Midnight of the first day 2003/08/03 is not included in the result. Midnight of the second day is included, even though the time specified is before midnight:

```
SELECT DATEDIFF( DAY, '2003/08/03 14:00', '2003/08/08 14:00' ) FROM iq_dummy
```

When you use month as the date part, DATEDIFF returns the number of first-of-the-months between two dates, including the second date but not the first. For example, both of the following statements return the value 9:

```
SELECT DATEDIFF( MONTH, '2003/02/01', '2003/11/15' ) FROM iq_dummy;
SELECT DATEDIFF( MONTH, '2003/02/01', '2003/11/01' ) FROM iq_dummy;
```

The first date 2003/02/01 is a first-of-month, but is not included in the result of either query. The second date 2003/11/01 in the second query is also a first-of-month and is included in the result.

When you use week as the date part, DATEDIFF returns the number of Sundays between the two dates, including the second date but not the first. For example, in the month 2003/08, the dates of the Sundays are 03, 10, 17, 24, and 31. The following query returns the value 4:

```
SELECT DATEDIFF( week, '2003/08/03', '2003/08/31' ) FROM iq_dummy;
```

The first Sunday \(2003/08/03\) is not included in the result.



### Data Lake Relational Engine Main Store Tables Versus Catalog Store Tables

DATEDIFF semantics differ between data lake Relational Engine main store tables and catalog store tables \(system tables\). The DATEDIFF results for time parts HOUR, MINUTE, SECOND, MILLISECOND, and MICROSECOND are calculated differently in certain situations.

Assume you have two time values three seconds apart: 11:14:59 and 11:15:02. Notice how the time range includes a minute boundary point \(11:15:00\).If you are requesting a difference unit type of MINUTE:

-   Main store table – data lake Relational Engine sees that the difference between the two time values is less than the MINUTE unit type, and calculates a DATEDIFF of 0.
-   Catalog store table – the system sees that the difference between the two time values is less than the MINUTE unit type, but notes that the difference includes the minute boundary point \(11:15:00\), and calculates a `DATEDIFF` of 1.

If you require catalog store DATEDIFF behavior in an expression that can be executed against either main store or catalog store tables, then execute the DATEDIFF over a CAST over a DATEFORMAT with an appropriate format string \(that doesn't include components smaller than the requested difference unit\) wrapped over each input:

```
DATEDIFF(MINUTE, 
             CAST(DATEFORMAT(t.col1, 'YYYY-MM-DD HH:NN’) AS TIMESTAMP), 
             CAST(DATEFORMAT(t.col2, 'YYYY-MM-DD HH:NN’) AS TIMESTAMP))
```



<a name="loioa545a63784f210158075c22cd6f85d3a__DATEDIFF_standards1"/>

## Standards and Compatibility

-   SQL – Transact-SQL extension to ISO/ANSI SQL grammar



<a name="loioa545a63784f210158075c22cd6f85d3a__DATEDIFF_examples1"/>

## Examples

-   The following statement returns 1:

    ```
    SELECT DATEDIFF( HOUR, '4:00AM', '5:50AM' )
    FROM iq_dummy
    ```

-   The following statement returns 102:

    ```
    SELECT DATEDIFF( MONTH, '1987/05/02', '1995/11/15' )
    FROM iq_dummy
    ```

-   The following statement returns 0:

    ```
    SELECT DATEDIFF( DAY, '00:00', '23:59' ) 
    FROM iq_dummy
    ```

-   The following statement returns 4:

    ```
    SELECT DATEDIFF( DAY, '1999/07/19 00:00', '1999/07/23
    23:59' ) FROM iq_dummy
    ```

-   The following statement returns 0:

    ```
    SELECT DATEDIFF( MONTH, '1999/07/19', '1999/07/23' )
    FROM iq_dummy
    ```

-   The following statement returns 1:

    ```
    SELECT DATEDIFF( MONTH, '1999/07/19', '1999/08/23' )
    FROM iq_dummy
    ```

-   The following statement returns 4:

    ```
    SELECT DATEDIFF(MCS, '2009-11-03 11:10:42.033185',
    '2009-11-03 11:10:42.033189') 
    FROM iq_dummy
    ```

-   The following statement returns 15:

    ```
    SELECT DATEDIFF(MICROSECOND, '2009-11-10
    14:57:52.722001', '2009-11-10 14:57:52.722016')
    FROM iq_dummy
    ```

-   The following statement returns 1,500,000:

    ```
    SELECT DATEDIFF(MCS, '2000/07/07/07 07:07:06.277777',
    '2000/07/07/07 07:07:07.777777') FROM iq_dummy
    ```


**Related Information**  


[DATEADD Function \[Date and Time\] for Data Lake Relational Engine](dateadd-function-date-and-time-for-data-lake-relational-engine-a5449de.md "Returns the date produced by adding the specified number of the specified date parts to a date.")

[DATECEILING Function \[Date and Time\] for Data Lake Relational Engine](dateceiling-function-date-and-time-for-data-lake-relational-engine-a545210.md "Calculates a new date, time, or datetime value by increasing the provided value up to the nearest larger value of the specified granularity.")

[DATEFLOOR Function \[Date and Time\] for Data Lake Relational Engine](datefloor-function-date-and-time-for-data-lake-relational-engine-a5462b6.md "Calculates a new date, time, or datetime value by reducing the provided value down to the nearest lower value of the specified multiple with the specified granularity.")

[DATENAME Function \[Date and Time\] for Data Lake Relational Engine](datename-function-date-and-time-for-data-lake-relational-engine-a5472b7.md "Returns the name of the specified part (such as the month “June”) of a date/time value, as a character string.")

[DATEPART Function \[Date and Time\] for Data Lake Relational Engine](datepart-function-date-and-time-for-data-lake-relational-engine-a547b06.md "Returns an integer value for the specified part of a date/time value.")

[DATEROUND Function \[Date and Time\] for Data Lake Relational Engine](dateround-function-date-and-time-for-data-lake-relational-engine-a5483a3.md "Calculates a new date, time, or datetime value by rounding the provided value up or down to the nearest multiple of the specified value with the specified granularity.")

[Date Parts in Data Lake Relational Engine](date-parts-in-data-lake-relational-engine-a52b8dd.md "Many of the date functions use dates built from date parts.")

[DATEDIFF Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/7bf7fa8d313a453c8bc224f2f29c65b5.html "Returns the interval between two dates.") :arrow_upper_right:

