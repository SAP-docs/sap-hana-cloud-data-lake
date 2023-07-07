<!-- loioc575f2fac8f94b1eaf49f8b8797a509f -->

# REMAINDER Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the remainder when one whole number is divided by another.



```
REMAINDER ( <dividend>, <divisor> )
```



<a name="loioc575f2fac8f94b1eaf49f8b8797a509f__section_bfp_w25_vrb"/>

## Parameters


<dl>
<dt><b>

*<dividend\>*

</b></dt>
<dd>

The dividend, or numerator of the division.



</dd><dt><b>

*<divisor\>*

</b></dt>
<dd>

The divisor, or denominator of the division.



</dd>
</dl>



<a name="loioc575f2fac8f94b1eaf49f8b8797a509f__section_zv3_ln3_wrb"/>

## Returns

-   INTEGER
-   NUMERIC



<a name="loioc575f2fac8f94b1eaf49f8b8797a509f__section_t3m_x25_vrb"/>

## Remarks

`REMAINDER` is the same as the `MOD` function.



<a name="loioc575f2fac8f94b1eaf49f8b8797a509f__section_hmf_y25_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar.
-   SAP database products – not supported by SAP Adaptive Server Enterprise. The % \(modulo\) operator and the division operator can be used to produce a remainder.



<a name="loioc575f2fac8f94b1eaf49f8b8797a509f__section_kfp_y25_vrb"/>

## Example

The following statement returns the value 2:

```
SELECT REMAINDER( 5, 3 ) FROM iq_dummy
```

**Related Information**  


[REMAINDER Function [Numeric] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a5788e7284f21015a4caecc7b2f96b10.html "Returns the remainder when one whole number is divided by another.") :arrow_upper_right:

