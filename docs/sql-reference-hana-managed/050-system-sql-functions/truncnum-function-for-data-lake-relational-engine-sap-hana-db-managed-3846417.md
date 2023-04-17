<!-- loio38464172958846abbb04ad86a7c02f65 -->

# TRUNCNUM Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Truncates a number at a specified number of places after the decimal point.



```
TRUNCNUM ( <numeric-expression>, <integer-expression> )
```



<a name="loio38464172958846abbb04ad86a7c02f65__section_lys_j3v_vrb"/>

## Parameters

 *<numeric-expression\>*
 :   The number to be truncated.

  *<integer-expression\>*
 :   A positive integer specifies the number of significant digits to the right of the decimal point at which to round. A negative expression specifies the number of significant digits to the left of the decimal point at which to round.

 

<a name="loio38464172958846abbb04ad86a7c02f65__section_ww2_k3v_vrb"/>

## Returns

NUMERIC



<a name="loio38464172958846abbb04ad86a7c02f65__section_pyn_k3v_vrb"/>

## Remarks

This function is the same as `TRUNCATE`, but does not cause keyword conflicts.

You can use combinations of `ROUND`, `FLOOR`, and `CEILING` to provide similar functionality.



<a name="loio38464172958846abbb04ad86a7c02f65__section_qsb_l3v_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loio38464172958846abbb04ad86a7c02f65__section_edc_m3v_vrb"/>

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


[TRUNCNUM Function [Numeric] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a58baf5b84f21015961fcdf7ec6e1b8b.html "Truncates a number at a specified number of places after the decimal point.") :arrow_upper_right:

