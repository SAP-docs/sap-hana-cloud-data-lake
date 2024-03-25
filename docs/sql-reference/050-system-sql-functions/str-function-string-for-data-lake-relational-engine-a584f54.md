<!-- loioa584f54284f21015bb43e961aa835036 -->

# STR Function \[String\] for Data Lake Relational Engine

Returns the string equivalent of a number.



```
STR ( <numeric-expression> [ , <length>[ , <decimal> ] ] );
```



<a name="loioa584f54284f21015bb43e961aa835036__STR_parm1"/>

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



<a name="loioa584f54284f21015bb43e961aa835036__STR_returns1"/>

## Result Set

VARCHAR



<a name="loioa584f54284f21015bb43e961aa835036__STR_remarks1"/>

## Remarks

If the integer portion of the number cannot fit in the length specified, then the result is NULL.



<a name="loioa584f54284f21015bb43e961aa835036__STR_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – compatible with SAP Adaptive Server Enterprise



<a name="loioa584f54284f21015bb43e961aa835036__STR_example1"/>

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


[STR Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/6152b1608e3e4c5e898c592f645366b7.html "Returns the string equivalent of a number.") :arrow_upper_right:

