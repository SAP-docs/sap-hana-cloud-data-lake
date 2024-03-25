<!-- loio488cdf45547747868ff78e55426175d9 -->

# MINUTES Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the number of minutes since an arbitrary date and time, the number of whole minutes between two specified times, or adds the specified integer-expression number of minutes to a time.



```
MINUTES ( <datetime-expression> 
| <datetime-expression>, <datetime-expression>
| <datetime-expression>, <integer-expression> );
```



<a name="loio488cdf45547747868ff78e55426175d9__section_ey4_hgn_vrb"/>

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

The number of minutes to be added to the *<datetime-expression\>*. If *<integer-expression\>* is negative, the appropriate number of minutes are subtracted from the date/time. If you supply an integer expression, the *<datetime-expression\>* must be explicitly cast as a `datetime` data type



</dd>
</dl>



<a name="loio488cdf45547747868ff78e55426175d9__section_nr2_3gn_vrb"/>

## Result Set

-   INT
-   TIMESTAMP



<a name="loio488cdf45547747868ff78e55426175d9__section_ytc_jgn_vrb"/>

## Remarks

The second syntax returns the number of whole minutes from the first date/time to the second date/time. The number might be negative.



<a name="loio488cdf45547747868ff78e55426175d9__section_bb5_jgn_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loio488cdf45547747868ff78e55426175d9__section_axg_kgn_vrb"/>

## Examples

-   Returns the value 1051125487:

    ```
    SELECT MINUTES( '1998-07-13 06:07:12' ) FROM iq_dummy;
    ```

-   Returns the value 240, to signify the difference between the two times:

    ```
    SELECT MINUTES( '1999-07-13 06:07:12',
    	'1999-07-13 10:07:12' ) FROM iq_dummy;
    ```

-   Returns the datetime value 1999-05-12 21:10:07.000:

    ```
    SELECT MINUTES( CAST( '1999-05-12 21:05:07'
    AS DATETIME ), 5) FROM iq_dummy;
    ```


**Related Information**  


[MINUTES Function \[Date and Time\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a5648d4484f21015975efebd7ac03399.html "Returns the number of minutes since an arbitrary date and time, the number of whole minutes between two specified times, or adds the specified integer-expression number of minutes to a time.") :arrow_upper_right:

