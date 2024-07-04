<!-- loio6c2f4cf7004b4f2cace1afa4889a44d0 -->

# CHAR Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the character with the ASCII value of a number.



```
CHAR ( <integer-expression> );
```



<a name="loio6c2f4cf7004b4f2cace1afa4889a44d0__section_wnw_ktl_srb"/>

## Parameters


<dl>
<dt><b>

*<integer-expression\>*

</b></dt>
<dd>

The number to be converted to an ASCII character. The number must be in the range 0 to 255, inclusive.



</dd>
</dl>



<a name="loio6c2f4cf7004b4f2cace1afa4889a44d0__section_etk_ltl_srb"/>

## Result Set

VARCHAR



<a name="loio6c2f4cf7004b4f2cace1afa4889a44d0__section_v41_mtl_srb"/>

## Remarks

The character in the current database character set corresponding to the supplied numeric expression modulo 256 is returned.

CHAR returns NULL for integer expressions with values greater than 255 or less than zero.



<a name="loio6c2f4cf7004b4f2cace1afa4889a44d0__section_yd4_mtl_srb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loio6c2f4cf7004b4f2cace1afa4889a44d0__section_ahb_ntl_srb"/>

## Examples

-   The following statement returns the value “Y”:

    ```
    SELECT CHAR( 89 ) FROM iq_dummy;
    ```

-   The following statement returns the value “S”:

    ```
    SELECT CHAR( 83 ) FROM iq_dummy;
    ```


**Related Information**  


[CHAR function \[String\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a53b50f084f210159a74ba4e4e50f914.html "Returns the character with the ASCII value of a number.") :arrow_upper_right:

