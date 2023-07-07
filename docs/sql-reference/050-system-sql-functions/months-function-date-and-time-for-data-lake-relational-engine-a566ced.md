<!-- loioa566ced484f21015ad419bb64c76680c -->

# MONTHS Function \[Date and Time\] for Data Lake Relational Engine

Returns the number of months since an arbitrary starting date/time or the number of months between two specified date/times, or adds the specified integer-expression number of months to a date/time.



```
MONTHS ( <date-expression>
| <date-expression, datetime-expression>
| <date-expression, integer-expression> )
```



<a name="loioa566ced484f21015ad419bb64c76680c__months_parma1"/>

## Parameters


<dl>
<dt><b>

*<date-expression\>*

</b></dt>
<dd>

A date and time.



</dd><dt><b>

*<integer-expression\>*

</b></dt>
<dd>

The number of months to be added to the *<date-expression\>*. If *<integer-expression\>* is negative, the appropriate number of months are subtracted from the date/time value. If you supply an integer expression, the *<date-expression\>* must be explicitly cast as a `datetime` data type.



</dd>
</dl>



<a name="loioa566ced484f21015ad419bb64c76680c__months_returns1"/>

## Returns

-   INT
-   TIMSTAMP



<a name="loioa566ced484f21015ad419bb64c76680c__months_results1"/>

## Remarks

The first syntax returns the number of months since an arbitrary starting date. This number is often useful for determining whether two date/time expressions are in the same month in the same year.

```
MONTHS( invoice_sent ) = MONTHS( payment_received )
```

Comparing the MONTH function would incorrectly include a payment made 12 months after the invoice was sent.

The second syntax returns the number of months from the first date to the second date. The number might be negative. It is calculated from the number of the first days of the month between the two dates. Hours, minutes and seconds are ignored.

The third syntax adds *<integer-expression\>* months to the given date. If the new date is past the end of the month — such as MONTHS \('1992-01-31', 1\) — the result is set to the last day of the month. If *<integer-expression\>* is negative, the appropriate number of months are subtracted from the date. Hours, minutes and seconds are ignored.



<a name="loioa566ced484f21015ad419bb64c76680c__months_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa566ced484f21015ad419bb64c76680c__months_examples1"/>

## Examples

-   The following statement returns the value 23982:

    ```
    SELECT MONTHS( '1998-07-13 06:07:12' ) FROM iq_dummy
    ```

-   The following statement returns the value 2, to signify the difference between the two dates:

    ```
    SELECT MONTHS( '1999-07-13 06:07:12',
    	'1999-09-13 10:07:12' ) FROM iq_dummy
    ```

-   The following statement returns the datetime value 1999-10-12 21:05:07.000:

    ```
    SELECT MONTHS( CAST( '1999-05-12 21:05:07'
    AS DATETIME ), 5) FROM iq_dummy
    ```


**Related Information**  


[CAST Function \[Data Type Conversion\] for Data Lake Relational Engine](cast-function-data-type-conversion-for-data-lake-relational-engine-a53996d.md "Returns the value of an expression converted to a supplied data type.")

[CONVERT Function \[Data Type Conversion\] for Data Lake Relational Engine](convert-function-data-type-conversion-for-data-lake-relational-engine-a53f6ef.md "Returns an expression converted to a supplied data type.")

[HOURS Function \[Date and Time\] for Data Lake Relational Engine](hours-function-date-and-time-for-data-lake-relational-engine-a556e14.md "Returns the number of hours since an arbitrary starting date and time, the number of whole hours between two specified times, or adds the specified integer-expression number of hours to a time.")

[MINUTES Function \[Date and Time\] for Data Lake Relational Engine](minutes-function-date-and-time-for-data-lake-relational-engine-a5648d4.md "Returns the number of minutes since an arbitrary date and time, the number of whole minutes between two specified times, or adds the specified integer-expression number of minutes to a time.")

[REPLACE Function \[String\] for Data Lake Relational Engine](replace-function-string-for-data-lake-relational-engine-a579952.md "Replaces all occurrences of a substring with another substring.")

[SECOND Function \[Date and Time\] for Data Lake Relational Engine](second-function-date-and-time-for-data-lake-relational-engine-a57dc03.md "Returns a number from 0 to 59 corresponding to the second component of the given date/time value.")

[WEEKS Function \[Date and Time\] for Data Lake Relational Engine](weeks-function-date-and-time-for-data-lake-relational-engine-a590601.md "Returns the number of weeks since an arbitrary starting date/time, returns the number of weeks between two specified date/times, or adds the specified integer-expression number of weeks to a date/time.")

[YEAR Function \[Date and Time\] for Data Lake Relational Engine](year-function-date-and-time-for-data-lake-relational-engine-a591eb9.md "Returns a 4-digit number corresponding to the year of the given date/time.")

[YEARS Function \[Date and Time\] for Data Lake Relational Engine](years-function-date-and-time-for-data-lake-relational-engine-a5926bf.md "Returns a 4-digit number corresponding to the year of a given date/time, returns the number of years between two specified date/times, or adds the specified integer-expression number of years to a date/time.")

[MONTHS Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/8c326df1855d47f2ad7c9a6a658b0db9.html "Returns the number of months since an arbitrary starting date/time or the number of months between two specified date/times, or adds the specified integer-expression number of months to a date/time.") :arrow_upper_right:

