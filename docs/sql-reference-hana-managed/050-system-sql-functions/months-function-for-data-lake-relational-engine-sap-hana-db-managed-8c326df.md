<!-- loio8c326df1855d47f2ad7c9a6a658b0db9 -->

# MONTHS Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the number of months since an arbitrary starting date/time or the number of months between two specified date/times, or adds the specified integer-expression number of months to a date/time.



```
MONTHS ( <date-expression>
| <date-expression, datetime-expression>
| <date-expression, integer-expression> );
```



<a name="loio8c326df1855d47f2ad7c9a6a658b0db9__section_i2x_h2n_vrb"/>

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



<a name="loio8c326df1855d47f2ad7c9a6a658b0db9__section_k4h_32n_vrb"/>

## Result Set

-   INT
-   TIMSTAMP



<a name="loio8c326df1855d47f2ad7c9a6a658b0db9__section_qvb_j2n_vrb"/>

## Remarks

The first syntax returns the number of months since an arbitrary starting date. This number is often useful for determining whether two date/time expressions are in the same month in the same year.

```
MONTHS( invoice_sent ) = MONTHS( payment_received );
```

Comparing the MONTH function would incorrectly include a payment made 12 months after the invoice was sent.

The second syntax returns the number of months from the first date to the second date. The number might be negative. It is calculated from the number of the first days of the month between the two dates. Hours, minutes and seconds are ignored.

The third syntax adds *<integer-expression\>* months to the given date. If the new date is past the end of the month — such as MONTHS \('1992-01-31', 1\) — the result is set to the last day of the month. If *<integer-expression\>* is negative, the appropriate number of months are subtracted from the date. Hours, minutes and seconds are ignored.



<a name="loio8c326df1855d47f2ad7c9a6a658b0db9__section_pnw_j2n_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loio8c326df1855d47f2ad7c9a6a658b0db9__section_qjh_k2n_vrb"/>

## Examples

-   The following statement returns the value 23982:

    ```
    SELECT MONTHS( '1998-07-13 06:07:12' ) FROM iq_dummy;
    ```

-   The following statement returns the value 2, to signify the difference between the two dates:

    ```
    SELECT MONTHS( '1999-07-13 06:07:12',
    	'1999-09-13 10:07:12' ) FROM iq_dummy;
    ```

-   The following statement returns the datetime value 1999-10-12 21:05:07.000:

    ```
    SELECT MONTHS( CAST( '1999-05-12 21:05:07'
    AS DATETIME ), 5) FROM iq_dummy;
    ```


**Related Information**  


[MONTHS Function \[Date and Time\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a566ced484f21015ad419bb64c76680c.html "Returns the number of months since an arbitrary starting date/time or the number of months between two specified date/times, or adds the specified integer-expression number of months to a date/time.") :arrow_upper_right:

