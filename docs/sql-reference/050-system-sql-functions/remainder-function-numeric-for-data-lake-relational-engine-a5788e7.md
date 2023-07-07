<!-- loioa5788e7284f21015a4caecc7b2f96b10 -->

# REMAINDER Function \[Numeric\] for Data Lake Relational Engine

Returns the remainder when one whole number is divided by another.



```
REMAINDER ( <dividend>, <divisor> )
```



<a name="loioa5788e7284f21015a4caecc7b2f96b10__REMAINDER_parm1"/>

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



<a name="loioa5788e7284f21015a4caecc7b2f96b10__REMAINDER_returns1"/>

## Returns

-   INTEGER
-   NUMERIC



<a name="loioa5788e7284f21015a4caecc7b2f96b10__REMAINDER_remarks1"/>

## Remarks

`REMAINDER` is the same as the `MOD` function.



<a name="loioa5788e7284f21015a4caecc7b2f96b10__REMAINDER_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar.
-   SAP database products – not supported by SAP Adaptive Server Enterprise. The % \(modulo\) operator and the division operator can be used to produce a remainder.



<a name="loioa5788e7284f21015a4caecc7b2f96b10__REMAINDER_example1"/>

## Example

The following statement returns the value 2:

```
SELECT REMAINDER( 5, 3 ) FROM iq_dummy
```

**Related Information**  


[MOD Function \[Numeric\] for Data Lake Relational Engine](mod-function-numeric-for-data-lake-relational-engine-a5650e7.md "Returns the remainder when one whole number is divided by another.")

[REMAINDER Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/c575f2fac8f94b1eaf49f8b8797a509f.html "Returns the remainder when one whole number is divided by another.") :arrow_upper_right:

