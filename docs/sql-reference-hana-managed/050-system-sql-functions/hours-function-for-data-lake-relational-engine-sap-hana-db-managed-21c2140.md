<!-- loio21c21405d89646019adb537e2ed90796 -->

# HOURS Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the number of hours since an arbitrary starting date and time, the number of whole hours between two specified times, or adds the specified integer-expression number of hours to a time.



```
HOURS ( <datetime-expression> 
| <datetime-expression>, <datetime-expression>
| <datetime-expression>, <integer-expression> );
```



<a name="loio21c21405d89646019adb537e2ed90796__section_nld_h4g_trb"/>

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



<a name="loio21c21405d89646019adb537e2ed90796__section_byp_h4g_trb"/>

## Result Set

INT



<a name="loio21c21405d89646019adb537e2ed90796__section_amc_34g_trb"/>

## Remarks

The second syntax returns the number of whole hours from the first date/time to the second date/time. The number might be negative.



<a name="loio21c21405d89646019adb537e2ed90796__section_ywp_34g_trb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loio21c21405d89646019adb537e2ed90796__section_fxz_34g_trb"/>

## Examples

-   The following statement returns the value 17518758:

    ```
    SELECT HOURS( '1998-07-13 06:07:12' ) FROM iq_dummy;
    ```

-   The following statement returns the value 4, to signify the difference between the two times:

    ```
    SELECT HOURS( '1999-07-13 06:07:12',
    	'1999-07-13 10:07:12' ) FROM iq_dummy;
    ```

-   The following statement returns the datetime value 1999-05-13 02:05:07.000:

    ```
    SELECT HOURS( CAST( '1999-05-12 21:05:07' 
    AS DATETIME ), 5 ) FROM iq_dummy;
    ```


**Related Information**  


[HOURS Function \[Date and Time\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a556e14084f210158443b519970bb86d.html "Returns the number of hours since an arbitrary starting date and time, the number of whole hours between two specified times, or adds the specified integer-expression number of hours to a time.") :arrow_upper_right:

