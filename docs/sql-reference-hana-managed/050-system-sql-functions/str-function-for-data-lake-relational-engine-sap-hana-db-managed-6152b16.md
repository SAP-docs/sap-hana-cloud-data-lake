<!-- loio6152b1608e3e4c5e898c592f645366b7 -->

# STR Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the string equivalent of a number.



```
STR ( <numeric-expression> [ , <length>[ , <decimal> ] ] );
```



<a name="loio6152b1608e3e4c5e898c592f645366b7__section_jf4_xt5_vrb"/>

## Parameters


<dl>
<dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

Any approximate numeric \(FLOAT, REAL, or DOUBLE precision\) expression.



</dd><dt><b>

*<length\>*

</b></dt>
<dd>

The number of characters to be returned \(including the decimal point, all digits to the right and left of the decimal point, the sign, if any, and blanks\). The default is 10 and the maximum length is 255.



</dd><dt><b>

*<decimal\>*

</b></dt>
<dd>

The number of digits to the right of the decimal point to be returned. The default is 0.



</dd>
</dl>



<a name="loio6152b1608e3e4c5e898c592f645366b7__section_nbc_yt5_vrb"/>

## Result Set

VARCHAR



<a name="loio6152b1608e3e4c5e898c592f645366b7__section_gfp_yt5_vrb"/>

## Remarks

If the integer portion of the number cannot fit in the length specified, then the result is NULL.



<a name="loio6152b1608e3e4c5e898c592f645366b7__section_y2b_zt5_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – compatible with SAP Adaptive Server Enterprise



<a name="loio6152b1608e3e4c5e898c592f645366b7__section_gsq_zt5_vrb"/>

## Examples

-   The following statement returns a string of six spaces followed by 1234, for a total of 10 characters:

    ```
    SELECT STR( 1234.56 ) FROM iq_dummy;
    ```

-   The following statement returns the result 1234.5:

    ```
    SELECT STR( 1234.56, 6, 1 ) FROM iq_dummy;
    ```

-   The following statement returns NULL because the integer portion of the number cannot fit in the specified length:

    ```
    SELECT STR( 1234.56, 3 ) FROM iq_dummy;
    ```


**Related Information**  


[STR Function \[String\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a584f54284f21015bb43e961aa835036.html "Returns the string equivalent of a number.") :arrow_upper_right:

