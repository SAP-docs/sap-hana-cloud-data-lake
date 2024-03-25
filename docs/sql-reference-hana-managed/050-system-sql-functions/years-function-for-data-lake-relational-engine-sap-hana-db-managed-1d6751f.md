<!-- loio1d6751f84bf14c8ca120407566bb798f -->

# YEARS Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns a 4-digit number corresponding to the year of a given date/time, returns the number of years between two specified date/times, or adds the specified integer-expression number of years to a date/time.




<dl>
<dt><b>

Syntax 1: Return the number of years between year 0000 and a TIMESTAMP value

</b></dt>
<dd>

```
YEARS( <timestamp-expression> );
```



</dd><dt><b>

Syntax 2: Return the number of years between two TIMESTAMP values

</b></dt>
<dd>

```
YEARS( <timestamp-expression>, <timestamp-expression> );
```



</dd><dt><b>

Syntax 3: Add years to a TIMESTAMP value

</b></dt>
<dd>

```
YEARS( <timestamp-expression>, <integer-expression> );
```



</dd>
</dl>



<a name="loio1d6751f84bf14c8ca120407566bb798f__section_lpg_4p3_wrb"/>

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

The number of years \(as a SMALLINT value\) to be added to *<timestamp-expression\>*. If *<integer-expression\>* is negative, the appropriate number of years are subtracted from *<timestamp-expression\>*. If you supply an *<integer-expression\>*, the *<timestamp-expression\>* must be explicitly cast as a DATE, TIME, or TIMESTAMP value. If *<timestamp-expression\>* is a TIME, the current year is assumed.



</dd>
</dl>



<a name="loio1d6751f84bf14c8ca120407566bb798f__section_aj2_lcv_vrb"/>

## Result Set

INTEGER \(SMALLINT\) when comparing two TIMESTAMP values.

TIMESTAMP when adding years to a TIMESTAMP value.



<a name="loio1d6751f84bf14c8ca120407566bb798f__section_hgr_ncv_vrb"/>

## Remarks

The `YEAR` function is the same as `YEARS` \(*<timestamp-expression\>*\).

For syntax 2, the value of YEARS is computed by counting the number of first days of the year between the two dates. The number might be negative. Hours, minutes, and seconds are ignored.

Syntax 3 adds an *<integer-expression\>* number of years to the given date. If the new date is past the end of the month \(such as `SELECT YEARS` \( `CAST` \( ‘1992-02-29’ AS `TIMESTAMP` \), 1 \)\), the result is set to the last day of the month. If *<integer-expression\>* is negative, the appropriate number of years is subtracted from the date. Hours, minutes, and seconds are ignored.



<a name="loio1d6751f84bf14c8ca120407566bb798f__section_kk3_4cv_vrb"/>

## Standards and compatibility

-   SQL—Vendor extension to ISO/ANSI SQL grammar.

-   SAP Database Products—Not supported by SAP Adaptive Server Enterprise.




<a name="loio1d6751f84bf14c8ca120407566bb798f__section_sc5_4cv_vrb"/>

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


[YEARS Function \[Date and Time\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a5926bf484f210159b3980226202882f.html "Returns a 4-digit number corresponding to the year of a given date/time, returns the number of years between two specified date/times, or adds the specified integer-expression number of years to a date/time.") :arrow_upper_right:

