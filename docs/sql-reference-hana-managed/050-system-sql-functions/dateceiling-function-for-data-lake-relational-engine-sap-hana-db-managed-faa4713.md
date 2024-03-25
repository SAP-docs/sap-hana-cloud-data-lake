<!-- loiofaa4713372c84096b66b27ab6204aa4f -->

# DATECEILING Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Calculates a new date, time, or datetime value by increasing the provided value up to the nearest larger value of the specified granularity.



```
DATECEILING ( <date-part>, <datetime-expression> [, <multiple-expression>] );
```



<a name="loiofaa4713372c84096b66b27ab6204aa4f__section_qsq_pfm_srb"/>

## Parameters


<dl>
<dt><b>

*<date-part\>*

</b></dt>
<dd>

The date part to be added to the date.



</dd><dt><b>

*<datetime-expression\>*

</b></dt>
<dd>

The date, time, or date-time expression containing the value you are evaluating.



</dd><dt><b>

*<multiple-expression\>*

</b></dt>
<dd>

\(Optional\) A nonzero positive integer value expression specifying how many multiples of the units specified by the date-part parameter to use within the calculation. For example, you can use multiple-expression to specify that you want to regularize your data to 200-microsecond intervals or 10-minute intervals.

If multiple-expression evaluates to zero, evaluates to a negative number, is an explicit NULL constant, or is not a valid value for the specified date-part, data lake Relational Engine generates an error. If multiple-expression evaluates to a NULL, then the function result is NULL.



</dd>
</dl>



<a name="loiofaa4713372c84096b66b27ab6204aa4f__section_qkg_qfm_srb"/>

## Remarks

This function calculates a new date, time, or datetime value by increasing the provided value up to the nearest larger value with the specified granularity. If you include the optional *<multiple-expression\>* parameter, then the function increases the date and time up to the nearest specified multiple of the specified granularity.

The data type of the calculated date and time matches the data type of the *<multiple-expression\>* parameter.

The following date parts are not compatible with DATECEILING:

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

For example, if you specify a multiple of two minutes, data lake Relational Engine applies two-minute intervals starting at the current hour.

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
    

If you specify a *<multiple-expression\>* for the day, week, month, quarter, or year date parts, data lake Relational Engine assumes the intervals started at the smallest date value \(0001-01-01\), smallest time value \(00:00:00.000000\), or smallest date-time value \(0001-01-01.00:00:00.000000\). For example, if you specify a multiple of 10 days, data lake Relational Engine calculates 10-day intervals starting at 0001-01-01.

For the day, week, month, quarter, or year date parts, you don't need to specify a multiple that divides evenly into the next larger unit of time granularity.

If data lake Relational Engine rounds to a multiple of the week date part, the date value is always Sunday.



<a name="loiofaa4713372c84096b66b27ab6204aa4f__section_ghw_qfm_srb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loiofaa4713372c84096b66b27ab6204aa4f__section_gzl_rfm_srb"/>

## Examples

-   This statement returns the value August 13, 2009 10:40.00.000AM:

    ```
    SELECT DATECEILING( MI, 'August 13, 2009, 10:32.00.132AM', 10)
     FROM iq_dummy;
    ```

-   This statement returns the value August 13, 2009 10:32.35.456800 AM:

    ```
    SELECT DATECEILING( US, 'August 13, 2009, 10:32.35.456789AM', 200 )
     FROM iq_dummy;
    ```

-   This statement returns the value August 13, 2009 10:32.35.600000 AM:

    ```
    SELECT DATECEILING( US, 'August 13, 2009, 10:32.35.456789AM', 200000 )
     FROM iq_dummy;
    ```

-   This statement returns the value August 13, 2009 10:32.35.456789 AM:

    ```
    SELECT DATECEILING( US, 'August 13, 2009, 10:32.35.456789AM')
     FROM iq_dummy;
    ```


**Related Information**  


[DATECEILING Function \[Date and Time\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a545210684f21015bfabb0f3f2ce3eae.html "Calculates a new date, time, or datetime value by increasing the provided value up to the nearest larger value of the specified granularity.") :arrow_upper_right:

