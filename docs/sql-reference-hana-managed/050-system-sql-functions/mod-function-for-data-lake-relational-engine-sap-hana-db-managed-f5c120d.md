<!-- loiof5c120d23a114a08951fed08d45fecc1 -->

# MOD Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the remainder when one whole number is divided by another.



```
MOD ( <dividend>, <divisor> );
```



<a name="loiof5c120d23a114a08951fed08d45fecc1__section_isy_5fn_vrb"/>

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



<a name="loiof5c120d23a114a08951fed08d45fecc1__section_hd5_vfn_vrb"/>

## Result Set

-   SMALLINT
-   INT
-   NUMERIC



<a name="loiof5c120d23a114a08951fed08d45fecc1__section_ly3_wfn_vrb"/>

## Remarks

Division involving a negative *<dividend\>* gives a negative or zero result. The sign of the *<divisor\>* has no effect.



<a name="loiof5c120d23a114a08951fed08d45fecc1__section_s4b_xfn_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loiof5c120d23a114a08951fed08d45fecc1__section_m1l_xfn_vrb"/>

## Example

The following statement returns the value 2:

```
SELECT MOD( 5, 3 ) FROM iq_dummy;
```

**Related Information**  


[MOD Function \[Numeric\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a5650e7684f21015b1dcafaf320a4d00.html "Returns the remainder when one whole number is divided by another.") :arrow_upper_right:

