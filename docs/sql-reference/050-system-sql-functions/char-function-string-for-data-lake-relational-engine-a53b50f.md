<!-- loioa53b50f084f210159a74ba4e4e50f914 -->

# CHAR function \[String\] for Data Lake Relational Engine

Returns the character with the ASCII value of a number.



```
CHAR ( <integer-expression> );
```



<a name="loioa53b50f084f210159a74ba4e4e50f914__CHAR_parm1"/>

## Parameters


<dl>
<dt><b>

*<integer-expression\>*

</b></dt>
<dd>

The number to be converted to an ASCII character. The number must be in the range 0 to 255, inclusive.



</dd>
</dl>



<a name="loioa53b50f084f210159a74ba4e4e50f914__CHAR_returns1"/>

## Result Set

VARCHAR



<a name="loioa53b50f084f210159a74ba4e4e50f914__CHAR_remarks1"/>

## Remarks

The character in the current database character set corresponding to the supplied numeric expression modulo 256 is returned.

CHAR returns NULL for integer expressions with values greater than 255 or less than zero.



<a name="loioa53b50f084f210159a74ba4e4e50f914__CHAR_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa53b50f084f210159a74ba4e4e50f914__CHAR_examples1"/>

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


[CHAR Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/6c2f4cf7004b4f2cace1afa4889a44d0.html "Returns the character with the ASCII value of a number.") :arrow_upper_right:

