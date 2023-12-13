<!-- loioa591eb9d84f210159e35a75b4b036a0d -->

# YEAR Function \[Date and Time\] for Data Lake Relational Engine

Returns a 4-digit number corresponding to the year of the given date/time.



```
YEAR ( <timestamp-expression> );
```



<a name="loioa591eb9d84f210159e35a75b4b036a0d__YEAR_parm1"/>

## Parameters


<dl>
<dt><b>

*<timestamp-expression\>*

</b></dt>
<dd>

A date and time.



</dd>
</dl>



<a name="loioa591eb9d84f210159e35a75b4b036a0d__YEAR_returns1"/>

## Result Set

SMALLINT



<a name="loioa591eb9d84f210159e35a75b4b036a0d__YEAR_remarks1"/>

## Remarks

The `YEAR` function is the same as the `YEARS` \(*<timestamp-expression\>*\) function.



<a name="loioa591eb9d84f210159e35a75b4b036a0d__YEAR_standards1"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioa591eb9d84f210159e35a75b4b036a0d__YEAR_example1"/>

## Example

The following statement returns the value 1998:

```
SELECT YEAR( '1998-07-13 06:07:12' ) FROM iq_dummy;
```

**Related Information**  


[NTILE Function \[Analytical\] for Data Lake Relational Engine](ntile-function-analytical-for-data-lake-relational-engine-a5695f3.md "Distributes query results into a specified number of buckets and assigns the bucket number to each row in the bucket.")

[CAST Function \[Data Type Conversion\] for Data Lake Relational Engine](cast-function-data-type-conversion-for-data-lake-relational-engine-a53996d.md "Returns the value of an expression converted to a supplied data type.")

[CONVERT Function \[Data Type Conversion\] for Data Lake Relational Engine](convert-function-data-type-conversion-for-data-lake-relational-engine-a53f6ef.md "Returns an expression converted to a supplied data type.")

[HOURS Function \[Date and Time\] for Data Lake Relational Engine](hours-function-date-and-time-for-data-lake-relational-engine-a556e14.md "Returns the number of hours since an arbitrary starting date and time, the number of whole hours between two specified times, or adds the specified integer-expression number of hours to a time.")

[MINUTES Function \[Date and Time\] for Data Lake Relational Engine](minutes-function-date-and-time-for-data-lake-relational-engine-a5648d4.md "Returns the number of minutes since an arbitrary date and time, the number of whole minutes between two specified times, or adds the specified integer-expression number of minutes to a time.")

[MONTHS Function \[Date and Time\] for Data Lake Relational Engine](months-function-date-and-time-for-data-lake-relational-engine-a566ced.md "Returns the number of months since an arbitrary starting date/time or the number of months between two specified date/times, or adds the specified integer-expression number of months to a date/time.")

[REPLACE Function \[String\] for Data Lake Relational Engine](replace-function-string-for-data-lake-relational-engine-a579952.md "Replaces all occurrences of a substring with another substring.")

[SECOND Function \[Date and Time\] for Data Lake Relational Engine](second-function-date-and-time-for-data-lake-relational-engine-a57dc03.md "Returns a number from 0 to 59 corresponding to the second component of the given date/time value.")

[WEEKS Function \[Date and Time\] for Data Lake Relational Engine](weeks-function-date-and-time-for-data-lake-relational-engine-a590601.md "Returns the number of weeks since an arbitrary starting date/time, returns the number of weeks between two specified date/times, or adds the specified integer-expression number of weeks to a date/time.")

[YEARS Function \[Date and Time\] for Data Lake Relational Engine](years-function-date-and-time-for-data-lake-relational-engine-a5926bf.md "Returns a 4-digit number corresponding to the year of a given date/time, returns the number of years between two specified date/times, or adds the specified integer-expression number of years to a date/time.")

[YEAR Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/54d4912c1eb74fccac5ded7c6fc9fa8d.html "Returns a 4-digit number corresponding to the year of the given date/time.") :arrow_upper_right:

