<!-- loio18801f8db2164f1ea0dfdfbe99a38520 -->

# SECONDS Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the number of seconds since an arbitrary starting date and time, the number of seconds between two times, or adds an integer amount of seconds to a time.



```
SECONDS ( <datetime-expression>
| <datetime-expression>, <datetime-expression>
| <datetime-expression>, <integer-expression> );
```



<a name="loio18801f8db2164f1ea0dfdfbe99a38520__section_mvb_pz5_vrb"/>

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



<a name="loio18801f8db2164f1ea0dfdfbe99a38520__section_esj_pz5_vrb"/>

## Result Set

-   INTEGER
-   TIMESTAMP



<a name="loio18801f8db2164f1ea0dfdfbe99a38520__section_mmw_pz5_vrb"/>

## Remarks

The second syntax returns the number of whole seconds from the first date/time to the second date/time. The number might be negative.



<a name="loio18801f8db2164f1ea0dfdfbe99a38520__section_orf_qz5_vrb"/>

## Standards and compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loio18801f8db2164f1ea0dfdfbe99a38520__section_n34_qz5_vrb"/>

## Examples

-   The following statement returns the value 3600:

    ```
    SELECT ( SECONDS( '1998-07-13 06:07:12' ) -
    SECONDS( '1998-07-13 05:07:12' )) FROM iq_dummy;
    ```

-   The following statement returns the value 14400, to signify the difference between the two times:

    ```
    SELECT SECONDS( '1999-07-13 06:07:12',
    	'1999-07-13 10:07:12' ) FROM iq_dummy;
    ```

-   The following statement returns the datetime value 1999-05-12 21:05:12.000:

    ```
    SELECT SECONDS( CAST( '1999-05-12 21:05:07'
    AS TIMESTAMP ), 5) FROM iq_dummy;
    ```


**Related Information**  


[SECONDS Function \[Date and Time\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a57e4e7d84f21015bdabf289394cd2ce.html "Returns the number of seconds since an arbitrary starting date and time, the number of seconds between two times, or adds an integer amount of seconds to a time.") :arrow_upper_right:

