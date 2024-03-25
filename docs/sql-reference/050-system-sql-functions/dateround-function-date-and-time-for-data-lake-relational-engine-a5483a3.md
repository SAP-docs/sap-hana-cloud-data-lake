<!-- loioa5483a3f84f21015ba1087485982b02f -->

# DATEROUND Function \[Date and Time\] for Data Lake Relational Engine

Calculates a new date, time, or datetime value by rounding the provided value up or down to the nearest multiple of the specified value with the specified granularity.



```
DATEROUND ( <date-part>, <datetime-expression> [, <multiple-expression> ] );
```



<a name="loioa5483a3f84f21015ba1087485982b02f__DATEROUND_parm1"/>

## Parameters


<dl>
<dt><b>

*<date-part\>*

</b></dt>
<dd>

The date part to be returned.



</dd><dt><b>

*<datetime-expression\>*

</b></dt>
<dd>

The date, time, or date-time expression containing the value you are evaluating.



</dd><dt><b>

*<multiple-expression\>*

</b></dt>
<dd>

\(Optional\).= A nonzero positive integer value expression specifying how many multiples of the units specified by date-part to use within the calculation. For example, you can use multiple-expression to specify that you want to regularize your data to 200-microsecond intervals or 10-minute intervals.

If *<multiple-expression\>* evaluates to zero, evaluates to a negative number, is an explicit NULL constant, or is not a valid value for the specified *<date-part\>*, then data lake Relational Engine generates an error. If *<multiple-expression\>* evaluates to a NULL, then the function result is NULL.



</dd>
</dl>



<a name="loioa5483a3f84f21015ba1087485982b02f__DATEROUND_remarks1"/>

## Remarks

This function calculates a new date, time, or datetime value by rounding the provided value up or down to the nearest value with the specified granularity. If you include the optional *<multiple-expression\>* parameter, then the function rounds the date and time to the nearest specified multiple of the specified granularity.

The data type of the calculated date and time matches the data type of the *<multiple-expression\>* parameter.

The following date parts are not compatible with `DATEROUND`:

-   DayofYear
-   WeekDay
-   CalYearofWeek
-   CalWeekofYear
-   CalDayofWeek

If you specify a *<multiple-expression\>* for the microsecond, millisecond, second, minute, or hour date parts, data lake Relational Engine assumes that the multiple applies from the start of the next larger unit of granularity:

-   Multiples of microsecond start from the current second
-   Multiples of millisecond start from the current second
-   Multiples of second start from the current minute
-   Multiples of minute start from the current hour
-   Multiples of hour start from the current day

For example, if you specify a multiple of two minutes, data lake Relational Engine applies two minute intervals starting at the current hour.

For the microsecond, millisecond, second, minute, and hour date parts, specify a *<multiple-expression\>* value that divides evenly into the range of the specified date part:

-   For hours – the valid *<multiple-expression\>* values are: 1, 2, 3, 4, 6, 8, 12, 24
-   For seconds and minutes – the valid *<multiple-expression\>* values are: 1, 2, 3, 4, 5, 6, 10, 12, 15, 20, 30, 60
-   For milliseconds – the valid *<multiple-expression\>* values are: 1, 2, 4, 5, 8, 10, 20, 25, 40, 50, 100, 125, 200, 250, 500, 1000
-   For microseconds – the valid *<multiple-expression\>* values are:


    <table>
    <tr>
    <td valign="top">
    
    -   1
    -   2
    -   4
    -   5
    -   8
    -   10
    -   16
    -   20
    -   25
    -   32


    
    </td>
    <td valign="top">
    
    -   40
    -   50
    -   64
    -   80
    -   100
    -   125
    -   160
    -   200
    -   250
    -   320


    
    </td>
    <td valign="top">
    
    -   400
    -   500
    -   625
    -   800
    -   1000
    -   1250
    -   1600
    -   2000
    -   2500
    -   3125


    
    </td>
    <td valign="top">
    
    -   4000
    -   5000
    -   6250
    -   8000
    -   10000
    -   12500
    -   15625
    -   20000
    -   25000
    -   31250


    
    </td>
    <td valign="top">
    
    -   40000
    -   50000
    -   62500
    -   100000
    -   125000
    -   200000
    -   250000
    -   500000
    -   1000000


    
    </td>
    </tr>
    </table>
    

If you specify a *<multiple-expression\>* for the day, week, month, quarter, or year date parts, data lake Relational Engine assumes the intervals started at the smallest date value \(0001-01-01\), smallest time value \(00:00:00.000000\), or smallest date-time value \(0001-01-01.00:00:00.000000\). For example, if you specify a multiple of 10 days, then data lake Relational Engine calculates 10-day intervals starting at 0001-01-01.

For the day, week, month, quarter, or year date parts, you don't need to specify a multiple that divides evenly into the next larger unit of time granularity.

If data lake Relational Engine rounds to a multiple of the week date part, then the date value is always Sunday.



<a name="loioa5483a3f84f21015ba1087485982b02f__DATEROUND_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa5483a3f84f21015ba1087485982b02f__DATEROUND_examples1"/>

## Examples

-   This statement returns the value August 13, 2009, 10:30.000AM:

    ```
    SELECT DATEROUND( MI, 'August 13, 2009 10:33.123AM', 10)
     FROM iq_dummy;
    ```

-   This statement returns the value August 13, 2009 10:32:35.456600 AM:

    ```
    SELECT DATEROUND( US, 'August 13, 2009, 10:32:35.456500AM', 200 )
     FROM iq_dummy;
    ```

-   This statement returns the value August 13, 2009 10:32:35.456789 AM:

    ```
    SELECT DATEROUND( US, 'August 13, 2009, 10:32:35.456789AM')
     FROM iq_dummy;
    ```

-   This statement returns the value August 13, 2009 10:32:35.456400 AM:

    ```
    SELECT DATEROUND( US, 'August 13, 2009, 10:32:35.456499AM', 200 )
     FROM iq_dummy;
    ```


**Related Information**  


[DATEADD Function \[Date and Time\] for Data Lake Relational Engine](dateadd-function-date-and-time-for-data-lake-relational-engine-a5449de.md "Returns the date produced by adding the specified number of the specified date parts to a date.")

[DATECEILING Function \[Date and Time\] for Data Lake Relational Engine](dateceiling-function-date-and-time-for-data-lake-relational-engine-a545210.md "Calculates a new date, time, or datetime value by increasing the provided value up to the nearest larger value of the specified granularity.")

[DATEDIFF Function \[Date and Time\] for Data Lake Relational Engine](datediff-function-date-and-time-for-data-lake-relational-engine-a545a63.md "Returns the interval between two dates.")

[DATEFLOOR Function \[Date and Time\] for Data Lake Relational Engine](datefloor-function-date-and-time-for-data-lake-relational-engine-a5462b6.md "Calculates a new date, time, or datetime value by reducing the provided value down to the nearest lower value of the specified multiple with the specified granularity.")

[DATENAME Function \[Date and Time\] for Data Lake Relational Engine](datename-function-date-and-time-for-data-lake-relational-engine-a5472b7.md "Returns the name of the specified part (such as the month “June”) of a date/time value, as a character string.")

[DATEPART Function \[Date and Time\] for Data Lake Relational Engine](datepart-function-date-and-time-for-data-lake-relational-engine-a547b06.md "Returns an integer value for the specified part of a date/time value.")

[Date Parts in Data Lake Relational Engine](date-parts-in-data-lake-relational-engine-a52b8dd.md "Many of the date functions use dates built from date parts.")

[DATEROUND Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/0e97cec264744399942b770e81700c0d.html "Calculates a new date, time, or datetime value by rounding the provided value up or down to the nearest multiple of the specified value with the specified granularity.") :arrow_upper_right:

