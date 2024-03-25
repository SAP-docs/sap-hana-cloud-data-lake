<!-- loioa57dc03b84f210158836c9258c67e700 -->

# SECOND Function \[Date and Time\] for Data Lake Relational Engine

Returns a number from 0 to 59 corresponding to the second component of the given date/time value.



```
SECOND ( <datetime-expression> );
```



<a name="loioa57dc03b84f210158836c9258c67e700__SECOND_parm1"/>

## Parameters


<dl>
<dt><b>

*<datetime-expression\>*

</b></dt>
<dd>

The date and time value.



</dd>
</dl>



<a name="loioa57dc03b84f210158836c9258c67e700__SECOND_returns1"/>

## Result Set

SMALLINT



<a name="loioa57dc03b84f210158836c9258c67e700__SECOND_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – compatible with SAP Adaptive Server Enterprise



<a name="loioa57dc03b84f210158836c9258c67e700__SECOND_examples1"/>

## Example

The following statement returns the value 5:

```
SELECT SECOND( '1998-07-13 08:21:05' ) FROM iq_dummy;
```

**Related Information**  


[CAST Function \[Data Type Conversion\] for Data Lake Relational Engine](cast-function-data-type-conversion-for-data-lake-relational-engine-a53996d.md "Returns the value of an expression converted to a supplied data type.")

[CONVERT Function \[Data Type Conversion\] for Data Lake Relational Engine](convert-function-data-type-conversion-for-data-lake-relational-engine-a53f6ef.md "Returns an expression converted to a supplied data type.")

[HOURS Function \[Date and Time\] for Data Lake Relational Engine](hours-function-date-and-time-for-data-lake-relational-engine-a556e14.md "Returns the number of hours since an arbitrary starting date and time, the number of whole hours between two specified times, or adds the specified integer-expression number of hours to a time.")

[MINUTES Function \[Date and Time\] for Data Lake Relational Engine](minutes-function-date-and-time-for-data-lake-relational-engine-a5648d4.md "Returns the number of minutes since an arbitrary date and time, the number of whole minutes between two specified times, or adds the specified integer-expression number of minutes to a time.")

[MONTHS Function \[Date and Time\] for Data Lake Relational Engine](months-function-date-and-time-for-data-lake-relational-engine-a566ced.md "Returns the number of months since an arbitrary starting date/time or the number of months between two specified date/times, or adds the specified integer-expression number of months to a date/time.")

[REPLACE Function \[String\] for Data Lake Relational Engine](replace-function-string-for-data-lake-relational-engine-a579952.md "Replaces all occurrences of a substring with another substring.")

[WEEKS Function \[Date and Time\] for Data Lake Relational Engine](weeks-function-date-and-time-for-data-lake-relational-engine-a590601.md "Returns the number of weeks since an arbitrary starting date/time, returns the number of weeks between two specified date/times, or adds the specified integer-expression number of weeks to a date/time.")

[YEAR Function \[Date and Time\] for Data Lake Relational Engine](year-function-date-and-time-for-data-lake-relational-engine-a591eb9.md "Returns a 4-digit number corresponding to the year of the given date/time.")

[YEARS Function \[Date and Time\] for Data Lake Relational Engine](years-function-date-and-time-for-data-lake-relational-engine-a5926bf.md "Returns a 4-digit number corresponding to the year of a given date/time, returns the number of years between two specified date/times, or adds the specified integer-expression number of years to a date/time.")

[SECOND Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/ff2ca422e5af48f58bd55ec839860dd4.html "Returns a number from 0 to 59 corresponding to the second component of the given date/time value.") :arrow_upper_right:

