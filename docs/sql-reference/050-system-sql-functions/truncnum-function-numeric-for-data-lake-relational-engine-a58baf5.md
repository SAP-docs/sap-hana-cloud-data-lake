<!-- loioa58baf5b84f21015961fcdf7ec6e1b8b -->

# TRUNCNUM Function \[Numeric\] for Data Lake Relational Engine

Truncates a number at a specified number of places after the decimal point.



```
TRUNCNUM ( <numeric-expression>, <integer-expression> )
```



<a name="loioa58baf5b84f21015961fcdf7ec6e1b8b__TRUNCNUM_parm1"/>

## Parameters


<dl>
<dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

The number to be truncated.



</dd><dt><b>

*<integer-expression\>*

</b></dt>
<dd>

A positive integer specifies the number of significant digits to the right of the decimal point at which to round. A negative expression specifies the number of significant digits to the left of the decimal point at which to round.



</dd>
</dl>



<a name="loioa58baf5b84f21015961fcdf7ec6e1b8b__TRUNCNUM_returns1"/>

## Returns

NUMERIC



<a name="loioa58baf5b84f21015961fcdf7ec6e1b8b__TRUNCNUM_remarks1"/>

## Remarks

This function is the same as `TRUNCATE`, but does not cause keyword conflicts.

You can use combinations of `ROUND`, `FLOOR`, and `CEILING` to provide similar functionality.



<a name="loioa58baf5b84f21015961fcdf7ec6e1b8b__TRUNCNUM_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioa58baf5b84f21015961fcdf7ec6e1b8b__TRUNCNUM_examples1"/>

## Examples

-   The following statement returns the value 600:

    ```
    SELECT TRUNCNUM( 655, -2 ) FROM iq_dummy
    ```

-   The following statement returns the value 655.340:

    ```
    SELECT TRUNCNUM( 655.348, 2 ) FROM iq_dummy
    ```


**Related Information**  


[ROUND Function \[Numeric\] for Data Lake Relational Engine](round-function-numeric-for-data-lake-relational-engine-a57bbb0.md "Rounds the numeric-expression to the specified integer-expression number of places after the decimal point.")

[TRUNCNUM Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/38464172958846abbb04ad86a7c02f65.html "Truncates a number at a specified number of places after the decimal point.") :arrow_upper_right:

