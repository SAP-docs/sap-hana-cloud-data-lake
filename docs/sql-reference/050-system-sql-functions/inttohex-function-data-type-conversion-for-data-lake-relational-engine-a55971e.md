<!-- loioa55971e984f21015845192079b46b239 -->

# INTTOHEX Function \[Data Type Conversion\] for Data Lake Relational Engine

Returns the hexadecimal equivalent of a decimal integer.



```
INTTOHEX ( <integer-expression> );
```



<a name="loioa55971e984f21015845192079b46b239__INTTOHEX_parm1"/>

## Parameters


<dl>
<dt><b>

*<integer-expression\>*

</b></dt>
<dd>

The integer to be converted to hexadecimal.



</dd>
</dl>



<a name="loioa55971e984f21015845192079b46b239__INTTOHEX_returns1"/>

## Result Set

VARCHAR



<a name="loioa55971e984f21015845192079b46b239__INTTOHEX_remarks1"/>

## Remarks

If data conversion of input to INTTOHEX conversion fails, data lake Relational Engine returns an error, unless the CONVERSION\_ERROR option is OFF. In that case, the result is NULL.



<a name="loioa55971e984f21015845192079b46b239__INTTOHEX_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa55971e984f21015845192079b46b239__INTTOHEX_eample1"/>

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


[INTTOHEX Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/cbe59f6c760e49a9ba1022e7d40f8642.html "Returns the hexadecimal equivalent of a decimal integer.") :arrow_upper_right:

