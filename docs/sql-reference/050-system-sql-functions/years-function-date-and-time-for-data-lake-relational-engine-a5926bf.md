<!-- loioa5926bf484f210159b3980226202882f -->

# YEARS Function \[Date and Time\] for Data Lake Relational Engine

Returns a 4-digit number corresponding to the year of a given date/time, returns the number of years between two specified date/times, or adds the specified integer-expression number of years to a date/time.



 Syntax 1: Return the number of years between year 0000 and a TIMESTAMP value
 :   ```
YEARS( <timestamp-expression> )
```

  Syntax 2: Return the number of years between two TIMESTAMP values
 :   ```
YEARS( <timestamp-expression>, <timestamp-expression> )
```

  Syntax 3: Add years to a TIMESTAMP value
 :   ```
YEARS( <timestamp-expression>, <integer-expression> )
```

 

<a name="loioa5926bf484f210159b3980226202882f__YEARS_parm1"/>

## Parameters

  *<timestamp-expression\>* 
 :   A date and time value of type TIMESTAMP.

  *<integer-expression\>*
 :   The number of years \(as a SMALLINT value\) to be added to *<timestamp-expression\>*. If *<integer-expression\>* is negative, the appropriate number of years are subtracted from *<timestamp-expression\>*. If you supply an *<integer-expression\>*, the *<timestamp-expression\>* must be explicitly cast as a DATE, TIME, or TIMESTAMP value. If *<timestamp-expression\>* is a TIME, the current year is assumed.

 

<a name="loioa5926bf484f210159b3980226202882f__YEARS_returs1"/>

## Returns

INTEGER \(SMALLINT\) when comparing two TIMESTAMP values.

TIMESTAMP when adding years to a TIMESTAMP value.



<a name="loioa5926bf484f210159b3980226202882f__YEARS_remarks1"/>

## Remarks

The `YEAR` function is the same as `YEARS` \(*<timestamp-expression\>*\).

For syntax 2, the value of YEARS is computed by counting the number of first days of the year between the two dates. The number might be negative. Hours, minutes, and seconds are ignored.

Syntax 3 adds an *<integer-expression\>* number of years to the given date. If the new date is past the end of the month \(such as `SELECT YEARS` \( `CAST` \( ‘1992-02-29’ AS `TIMESTAMP` \), 1 \)\), the result is set to the last day of the month. If *<integer-expression\>* is negative, the appropriate number of years is subtracted from the date. Hours, minutes, and seconds are ignored.



<a name="loioa5926bf484f210159b3980226202882f__YEARS_standards1"/>

## Standards and compatibility

-   SQL—Vendor extension to ISO/ANSI SQL grammar.

-   SAP Database Products—Not supported by SAP Adaptive Server Enterprise.




<a name="loioa5926bf484f210159b3980226202882f__YEARS_examples1"/>

## Examples

-   The following statement returns the value 1998:

    ```
    SELECT YEARS( '1998-07-13 06:07:12' ) FROM iq_dummy;
    ```

-   The following statement returns the value 2, to signify the difference between the two dates.

    ```
    SELECT YEARS( '1997-07-13 06:07:12',
    	'1999-09-13 10:07:12' ) FROM iq_dummy;
    ```

-   The following statement returns the value 2004-05-12 21:05:07.000.

    ```
    SELECT YEARS( CAST( '1999-05-12 21:05:07'
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

[WEEKS Function \[Date and Time\] for Data Lake Relational Engine](weeks-function-date-and-time-for-data-lake-relational-engine-a590601.md "Returns the number of weeks since an arbitrary starting date/time, returns the number of weeks between two specified date/times, or adds the specified integer-expression number of weeks to a date/time.")

[YEAR Function \[Date and Time\] for Data Lake Relational Engine](year-function-date-and-time-for-data-lake-relational-engine-a591eb9.md "Returns a 4-digit number corresponding to the year of the given date/time.")

[YEARS Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/1d6751f84bf14c8ca120407566bb798f.html "Returns a 4-digit number corresponding to the year of a given date/time, returns the number of years between two specified date/times, or adds the specified integer-expression number of years to a date/time.") :arrow_upper_right:

