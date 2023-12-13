<!-- loioa590601384f210158a02bf2d5a2c1783 -->

# WEEKS Function \[Date and Time\] for Data Lake Relational Engine

Returns the number of weeks since an arbitrary starting date/time, returns the number of weeks between two specified date/times, or adds the specified integer-expression number of weeks to a date/time.




<dl>
<dt><b>

Syntax 1: Return the number of weeks between year 0000 and a TIMESTAMP value

</b></dt>
<dd>

```
WEEKS( <timestamp-expression> );
```



</dd><dt><b>

Syntax 2: Return the number of weeks between two TIMESTAMP values

</b></dt>
<dd>

```
WEEKS( <timestamp-expression>, <timestamp-expression> );
```



</dd><dt><b>

Syntax 3: Add years to a TIMESTAMP value

</b></dt>
<dd>

```
WEEKS( <timestamp-expression>, <integer-expression> );
```



</dd>
</dl>



<a name="loioa590601384f210158a02bf2d5a2c1783__WEEKS_parm1"/>

## Parameters


<dl>
<dt><b>

*<timestamp-expression\>* 

</b></dt>
<dd>

A date and time value of type TIMESTAMP.



</dd><dt><b>

*<integer-expression\>*

</b></dt>
<dd>

The number of weeks \(as a SMALLINT value\) to be added to the *<timestamp-expression\>*. If *<integer-expression\>* is negative, the appropriate number of weeks are subtracted from the date/time*<timestamp-expression\>*. Hours, minutes, and seconds are ignored. If you supply an integer expression, the *<timestamp-expression\>* must be explicitly cast as a `DATETIME` data type.



</dd>
</dl>



<a name="loioa590601384f210158a02bf2d5a2c1783__WEEKS_returns1"/>

## Result Set

INTEGER \(SMALLINT\) when comparing two TIMESTAMP values.

TIMESTAMP when adding weeks to a TIMESTAMP value.



<a name="loioa590601384f210158a02bf2d5a2c1783__WEEKS_remarks1"/>

## Remarks

Weeks are defined as going from Sunday to Saturday, as they do in a North American calendar. The number returned by the first syntax is often useful for determining if two dates are in the same week:

```
WEEKS ( invoice_sent ) = WEEKS ( payment_received ) FROM iq_dummy;
```

For syntax 2, the value of WEEKS is calculated from the number of Sundays between the two dates. Hours, minutes, and seconds are ignored.



<a name="loioa590601384f210158a02bf2d5a2c1783__WEEKS_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioa590601384f210158a02bf2d5a2c1783__WEEKS_examples1"/>

## Examples

-   The following statement returns the value 104278:

    ```
    SELECT WEEKS( '1998-07-13 06:07:12' ) FROM iq_dummy;
    ```

-   The following statement returns the value 9, to signify the difference between the two dates:

    ```
    SELECT WEEKS( '1999-07-13 06:07:12',
    	'1999-09-13 10:07:12' ) FROM iq_dummy;
    ```

-   The following statement returns the timestamp value 1999-06-16 21:05:07.000:

    ```
    SELECT WEEKS( CAST( '1999-05-12 21:05:07'
    AS TIMESTAMP ), 5) FROM iq_dummy;
    ```


**Related Information**  


[CAST Function \[Data Type Conversion\] for Data Lake Relational Engine](cast-function-data-type-conversion-for-data-lake-relational-engine-a53996d.md "Returns the value of an expression converted to a supplied data type.")

[CONVERT Function \[Data Type Conversion\] for Data Lake Relational Engine](convert-function-data-type-conversion-for-data-lake-relational-engine-a53f6ef.md "Returns an expression converted to a supplied data type.")

[HOURS Function \[Date and Time\] for Data Lake Relational Engine](hours-function-date-and-time-for-data-lake-relational-engine-a556e14.md "Returns the number of hours since an arbitrary starting date and time, the number of whole hours between two specified times, or adds the specified integer-expression number of hours to a time.")

[MINUTES Function \[Date and Time\] for Data Lake Relational Engine](minutes-function-date-and-time-for-data-lake-relational-engine-a5648d4.md "Returns the number of minutes since an arbitrary date and time, the number of whole minutes between two specified times, or adds the specified integer-expression number of minutes to a time.")

[MONTHS Function \[Date and Time\] for Data Lake Relational Engine](months-function-date-and-time-for-data-lake-relational-engine-a566ced.md "Returns the number of months since an arbitrary starting date/time or the number of months between two specified date/times, or adds the specified integer-expression number of months to a date/time.")

[REPLACE Function \[String\] for Data Lake Relational Engine](replace-function-string-for-data-lake-relational-engine-a579952.md "Replaces all occurrences of a substring with another substring.")

[SECOND Function \[Date and Time\] for Data Lake Relational Engine](second-function-date-and-time-for-data-lake-relational-engine-a57dc03.md "Returns a number from 0 to 59 corresponding to the second component of the given date/time value.")

[YEAR Function \[Date and Time\] for Data Lake Relational Engine](year-function-date-and-time-for-data-lake-relational-engine-a591eb9.md "Returns a 4-digit number corresponding to the year of the given date/time.")

[YEARS Function \[Date and Time\] for Data Lake Relational Engine](years-function-date-and-time-for-data-lake-relational-engine-a5926bf.md "Returns a 4-digit number corresponding to the year of a given date/time, returns the number of years between two specified date/times, or adds the specified integer-expression number of years to a date/time.")

[WEEKS Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/1bad0c474fc14fa299ff73a738157073.html "Returns the number of weeks since an arbitrary starting date/time, returns the number of weeks between two specified date/times, or adds the specified integer-expression number of weeks to a date/time.") :arrow_upper_right:

