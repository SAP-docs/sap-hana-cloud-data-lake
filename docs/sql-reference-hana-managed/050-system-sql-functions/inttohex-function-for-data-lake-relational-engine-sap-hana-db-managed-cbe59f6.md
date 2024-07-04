<!-- loiocbe59f6c760e49a9ba1022e7d40f8642 -->

# INTTOHEX Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the hexadecimal equivalent of a decimal integer.



```
INTTOHEX ( <integer-expression> );
```



<a name="loiocbe59f6c760e49a9ba1022e7d40f8642__section_rbn_34h_trb"/>

## Parameters


<dl>
<dt><b>

*<integer-expression\>*

</b></dt>
<dd>

The integer to be converted to hexadecimal.



</dd>
</dl>



<a name="loiocbe59f6c760e49a9ba1022e7d40f8642__section_jcb_j4h_trb"/>

## Result Set

VARCHAR



<a name="loiocbe59f6c760e49a9ba1022e7d40f8642__section_jss_p4h_trb"/>

## Remarks

If data conversion of input to INTTOHEX conversion fails, data lake Relational Engine returns an error, unless the CONVERSION\_ERROR option is OFF. In that case, the result is NULL.



<a name="loiocbe59f6c760e49a9ba1022e7d40f8642__section_cst_q4h_trb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loiocbe59f6c760e49a9ba1022e7d40f8642__section_tld_r4h_trb"/>

## Examples

-   The following statement returns the value 3B9ACA00:

    ```
    SELECT INTTOHEX( 1000000000 ) FROM iq_dummy;
    ```

-   The following statement returns the value 00000002540BE400:

    ```
    SELECT INTTOHEX ( 10000000000) FROM iq_dummy;
    ```


**Related Information**  


[INTTOHEX Function \[Data Type Conversion\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a55971e984f21015845192079b46b239.html "Returns the hexadecimal equivalent of a decimal integer.") :arrow_upper_right:

