<!-- loio1bad0c474fc14fa299ff73a738157073 -->

# WEEKS Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the number of weeks since an arbitrary starting date/time, returns the number of weeks between two specified date/times, or adds the specified integer-expression number of weeks to a date/time.




<dl>
<dt><b>

Syntax 1: Return the number of weeks between year 0000 and a TIMESTAMP value

</b></dt>
<dd>

```
WEEKS( <timestamp-expression> )
```



</dd><dt><b>

Syntax 2: Return the number of weeks between two TIMESTAMP values

</b></dt>
<dd>

```
WEEKS( <timestamp-expression>, <timestamp-expression> )
```



</dd><dt><b>

Syntax 3: Add years to a TIMESTAMP value

</b></dt>
<dd>

```
WEEKS( <timestamp-expression>, <integer-expression> )
```



</dd>
</dl>



<a name="loio1bad0c474fc14fa299ff73a738157073__section_ijx_f2v_vrb"/>

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

The number of weeks \(as a SMALLINT value\) to be added to the *<timestamp-expression\>*. If *<integer-expression\>* is negative, the appropriate number of weeks are subtracted from the date/time*<timestamp-expression\>*. Hours, minutes, and seconds are ignored. If you supply an integer expression, the *<timestamp-expression\>* must be explicitly cast as a `DATETIME` data type.



</dd>
</dl>



<a name="loio1bad0c474fc14fa299ff73a738157073__section_pzy_h2v_vrb"/>

## Returns

INTEGER \(SMALLINT\) when comparing two TIMESTAMP values.

TIMESTAMP when adding weeks to a TIMESTAMP value.



<a name="loio1bad0c474fc14fa299ff73a738157073__section_omp_j2v_vrb"/>

## Remarks

Weeks are defined as going from Sunday to Saturday, as they do in a North American calendar. The number returned by the first syntax is often useful for determining if two dates are in the same week:

```
WEEKS ( invoice_sent ) = WEEKS ( payment_received ) FROM iq_dummy
```

For syntax 2, the value of WEEKS is calculated from the number of Sundays between the two dates. Hours, minutes, and seconds are ignored.This function is not affected by the DATE\_FIRST\_DAY\_OF\_WEEK option.



<a name="loio1bad0c474fc14fa299ff73a738157073__section_ywx_j2v_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loio1bad0c474fc14fa299ff73a738157073__section_jbq_3p3_wrb"/>

## Examples

-   The following statement returns the value 104278:

    ```
    SELECT WEEKS( '1998-07-13 06:07:12' ) FROM iq_dummy
    ```

-   The following statement returns the value 9, to signify the difference between the two dates:

    ```
    SELECT WEEKS( '1999-07-13 06:07:12',
    	'1999-09-13 10:07:12' ) FROM iq_dummy
    ```

-   The following statement returns the timestamp value 1999-06-16 21:05:07.000:

    ```
    SELECT WEEKS( CAST( '1999-05-12 21:05:07'
    AS TIMESTAMP ), 5) FROM iq_dummy
    ```


**Related Information**  


[WEEKS Function [Date and Time] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a590601384f210158a02bf2d5a2c1783.html "Returns the number of weeks since an arbitrary starting date/time, returns the number of weeks between two specified date/times, or adds the specified integer-expression number of weeks to a date/time.") :arrow_upper_right:

