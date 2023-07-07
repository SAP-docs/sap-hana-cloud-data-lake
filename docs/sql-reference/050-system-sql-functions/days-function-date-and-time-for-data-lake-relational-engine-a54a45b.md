<!-- loioa54a45b584f21015a4c2ab2c117fc738 -->

# DAYS Function \[Date and Time\] for Data Lake Relational Engine

Returns the number of days since an arbitrary starting date, returns the number of days between two specified dates, or adds the specified *<integer-expression\>* number of days to a given date.



```
DAYS ( <datetime-expression> )
  | ( <datetime-expression>, <datetime-expression> )
  | ( <datetime-expression>, <integer-expression> )
```



<a name="loioa54a45b584f21015a4c2ab2c117fc738__DAYS_parm1"/>

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

The number of days to be added to the *<datetime-expression\>*. If the *<integer-expression\>* is negative, the appropriate number of days are subtracted from the date and time. If you supply an integer expression, the *<datetime-expression\>* must be explicitly cast as a date.



</dd>
</dl>



<a name="loioa54a45b584f21015a4c2ab2c117fc738__DAYS_returns1"/>

## Returns

INT when you specify two datetime expressions.

TIMESTAMP when the second argument you specify is an integer.



<a name="loioa54a45b584f21015a4c2ab2c117fc738__DAYS_remarks1"/>

## Remarks

`DAYS` ignores hours, minutes, and seconds.



<a name="loioa54a45b584f21015a4c2ab2c117fc738__DAYS_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa54a45b584f21015a4c2ab2c117fc738__DAYS_examples1"/>

## Examples

-   The following statement returns the integer value 729948:

    ```
    SELECT DAYS( '1998-07-13 06:07:12' ) FROM iq_dummy
    ```

-   The following statement returns the integer value -366, which is the difference between the two dates:

    ```
    SELECT DAYS( '1998-07-13 06:07:12',
    '1997-07-12 10:07:12' ) FROM iq_dummy
    ```

-   The following statement returns the value 1999-07-14:

    ```
    SELECT DAYS( CAST('1998-07-13' AS DATE ), 366 )
    FROM iq_dummy
    ```


**Related Information**  


[CAST Function \[Data Type Conversion\] for Data Lake Relational Engine](cast-function-data-type-conversion-for-data-lake-relational-engine-a53996d.md "Returns the value of an expression converted to a supplied data type.")

[DAYS Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/80456cf5652446c4b1279d5fb21e21dd.html "Returns the number of days since an arbitrary starting date, returns the number of days between two specified dates, or adds the specified integer-expression number of days to a given date.") :arrow_upper_right:

