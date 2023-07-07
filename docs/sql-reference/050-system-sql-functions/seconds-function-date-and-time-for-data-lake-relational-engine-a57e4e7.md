<!-- loioa57e4e7d84f21015bdabf289394cd2ce -->

# SECONDS Function \[Date and Time\] for Data Lake Relational Engine

Returns the number of seconds since an arbitrary starting date and time, the number of seconds between two times, or adds an integer amount of seconds to a time.



```
SECONDS ( <datetime-expression>
| <datetime-expression>, <datetime-expression>
| <datetime-expression>, <integer-expression> )
```



<a name="loioa57e4e7d84f21015bdabf289394cd2ce__SECONDS_parm1"/>

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

The number of seconds to be added to the *<datetime-expression\>*. If *<integer-expression\>* is negative, the appropriate number of minutes are subtracted from the date/time value. If you supply an integer expression, the *<datetime-expression\>* must be explicitly cast as a datetime data type.



</dd>
</dl>



<a name="loioa57e4e7d84f21015bdabf289394cd2ce__SECONDS_returns1"/>

## Returns

-   INTEGER
-   TIMESTAMP



<a name="loioa57e4e7d84f21015bdabf289394cd2ce__SECONDS_remarks1"/>

## Remarks

The second syntax returns the number of whole seconds from the first date/time to the second date/time. The number might be negative.



<a name="loioa57e4e7d84f21015bdabf289394cd2ce__SECONDS_standards1"/>

## Standards and compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioa57e4e7d84f21015bdabf289394cd2ce__SECONDS_examples1"/>

## Examples

-   The following statement returns the value 3600:

    ```
    SELECT ( SECONDS( '1998-07-13 06:07:12' ) -
    SECONDS( '1998-07-13 05:07:12' )) FROM iq_dummy
    ```

-   The following statement returns the value 14400, to signify the difference between the two times:

    ```
    SELECT SECONDS( '1999-07-13 06:07:12',
    	'1999-07-13 10:07:12' ) FROM iq_dummy
    ```

-   The following statement returns the datetime value 1999-05-12 21:05:12.000:

    ```
    SELECT SECONDS( CAST( '1999-05-12 21:05:07'
    AS TIMESTAMP ), 5) FROM iq_dummy
    ```


**Related Information**  


[SECONDS Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/18801f8db2164f1ea0dfdfbe99a38520.html "Returns the number of seconds since an arbitrary starting date and time, the number of seconds between two times, or adds an integer amount of seconds to a time.") :arrow_upper_right:

