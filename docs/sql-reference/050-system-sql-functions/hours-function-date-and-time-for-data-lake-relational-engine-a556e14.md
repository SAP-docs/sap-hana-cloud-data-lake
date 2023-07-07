<!-- loioa556e14084f210158443b519970bb86d -->

# HOURS Function \[Date and Time\] for Data Lake Relational Engine

Returns the number of hours since an arbitrary starting date and time, the number of whole hours between two specified times, or adds the specified integer-expression number of hours to a time.



```
HOURS ( <datetime-expression> 
| <datetime-expression>, <datetime-expression>
| <datetime-expression>, <integer-expression> )
```



<a name="loioa556e14084f210158443b519970bb86d__HOURS_parm1"/>

## Parameters


<dl>
<dt><b>

*<datetime-expression\>*

</b></dt>
<dd>

A date and time.



</dd><dt><b>

*<integer-expression\>*

</b></dt>
<dd>

The number of hours to be added to the *<datetime-expression\>*. If *<integer-expression\>* is negative, the appropriate number of hours are subtracted from the date/time. If you supply an integer expression, the *<datetime-expression\>* must be explicitly cast as a datetime data type.



</dd>
</dl>



<a name="loioa556e14084f210158443b519970bb86d__HOURS_returns1"/>

## Returns

INT



<a name="loioa556e14084f210158443b519970bb86d__HOURS_remarks1"/>

## Remarks

The second syntax returns the number of whole hours from the first date/time to the second date/time. The number might be negative.



<a name="loioa556e14084f210158443b519970bb86d__HOURS_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa556e14084f210158443b519970bb86d__HOURS_examples1"/>

## Examples

-   The following statement returns the value 17518758:

    ```
    SELECT HOURS( '1998-07-13 06:07:12' ) FROM iq_dummy
    ```

-   The following statement returns the value 4, to signify the difference between the two times:

    ```
    SELECT HOURS( '1999-07-13 06:07:12',
    	'1999-07-13 10:07:12' ) FROM iq_dummy
    ```

-   The following statement returns the datetime value 1999-05-13 02:05:07.000:

    ```
    SELECT HOURS( CAST( '1999-05-12 21:05:07' 
    AS DATETIME ), 5 ) FROM iq_dummy
    ```


**Related Information**  


[CAST Function \[Data Type Conversion\] for Data Lake Relational Engine](cast-function-data-type-conversion-for-data-lake-relational-engine-a53996d.md "Returns the value of an expression converted to a supplied data type.")

[CONVERT Function \[Data Type Conversion\] for Data Lake Relational Engine](convert-function-data-type-conversion-for-data-lake-relational-engine-a53f6ef.md "Returns an expression converted to a supplied data type.")

[MINUTES Function \[Date and Time\] for Data Lake Relational Engine](minutes-function-date-and-time-for-data-lake-relational-engine-a5648d4.md "Returns the number of minutes since an arbitrary date and time, the number of whole minutes between two specified times, or adds the specified integer-expression number of minutes to a time.")

[MONTHS Function \[Date and Time\] for Data Lake Relational Engine](months-function-date-and-time-for-data-lake-relational-engine-a566ced.md "Returns the number of months since an arbitrary starting date/time or the number of months between two specified date/times, or adds the specified integer-expression number of months to a date/time.")

[REPLACE Function \[String\] for Data Lake Relational Engine](replace-function-string-for-data-lake-relational-engine-a579952.md "Replaces all occurrences of a substring with another substring.")

[SECOND Function \[Date and Time\] for Data Lake Relational Engine](second-function-date-and-time-for-data-lake-relational-engine-a57dc03.md "Returns a number from 0 to 59 corresponding to the second component of the given date/time value.")

[WEEKS Function \[Date and Time\] for Data Lake Relational Engine](weeks-function-date-and-time-for-data-lake-relational-engine-a590601.md "Returns the number of weeks since an arbitrary starting date/time, returns the number of weeks between two specified date/times, or adds the specified integer-expression number of weeks to a date/time.")

[YEAR Function \[Date and Time\] for Data Lake Relational Engine](year-function-date-and-time-for-data-lake-relational-engine-a591eb9.md "Returns a 4-digit number corresponding to the year of the given date/time.")

[YEARS Function \[Date and Time\] for Data Lake Relational Engine](years-function-date-and-time-for-data-lake-relational-engine-a5926bf.md "Returns a 4-digit number corresponding to the year of a given date/time, returns the number of years between two specified date/times, or adds the specified integer-expression number of years to a date/time.")

[HOURS Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/21c21405d89646019adb537e2ed90796.html "Returns the number of hours since an arbitrary starting date and time, the number of whole hours between two specified times, or adds the specified integer-expression number of hours to a time.") :arrow_upper_right:

