<!-- loioa5650e7684f21015b1dcafaf320a4d00 -->

# MOD Function \[Numeric\] for Data Lake Relational Engine

Returns the remainder when one whole number is divided by another.



```
MOD ( <dividend>, <divisor> );
```



<a name="loioa5650e7684f21015b1dcafaf320a4d00__MOD_parm1"/>

## Parameters


<dl>
<dt><b>

*<dividend\>*

</b></dt>
<dd>

The dividend, or numerator, of the division.



</dd><dt><b>

*<divisor\>*

</b></dt>
<dd>

The divisor, or denominator, of the division.



</dd>
</dl>



<a name="loioa5650e7684f21015b1dcafaf320a4d00__MOD_returns1"/>

## Result Set

-   SMALLINT
-   INT
-   NUMERIC



<a name="loioa5650e7684f21015b1dcafaf320a4d00__MOD_remarks1"/>

## Remarks

Division involving a negative *<dividend\>* gives a negative or zero result. The sign of the *<divisor\>* has no effect.



<a name="loioa5650e7684f21015b1dcafaf320a4d00__MOD_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa5650e7684f21015b1dcafaf320a4d00__MOD_examples1"/>

## Examples

The following statement returns the value 2:

```
SELECT MOD( 5, 3 ) FROM iq_dummy;
```

**Related Information**  


[REMAINDER Function \[Numeric\] for Data Lake Relational Engine](remainder-function-numeric-for-data-lake-relational-engine-a5788e7.md "Returns the remainder when one whole number is divided by another.")

[MOD Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/f5c120d23a114a08951fed08d45fecc1.html "Returns the remainder when one whole number is divided by another.") :arrow_upper_right:

