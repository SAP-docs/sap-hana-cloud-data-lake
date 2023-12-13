<!-- loioa54c87d684f21015a9b9f518179a73ff -->

# DEGREES Function \[Numeric\] for Data Lake Relational Engine

Converts a number from radians to degrees.



```
DEGREES ( <numeric-expression> );
```



<a name="loioa54c87d684f21015a9b9f518179a73ff__DEGREES_parm1"/>

## Parameters


<dl>
<dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

An angle in radians.



</dd>
</dl>



<a name="loioa54c87d684f21015a9b9f518179a73ff__DEGREES_resturns1"/>

## Result Set

Returns the degrees of the angle given by *<numeric-expression\>*.

DOUBLE



<a name="loioa54c87d684f21015a9b9f518179a73ff__DEGREES_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa54c87d684f21015a9b9f518179a73ff__DEGREES_examples1"/>

## Example

The following statement returns the value 29.793805:

```
SELECT DEGREES( 0.52 ) FROM iq_dummy;
```

**Related Information**  


[DEGREES Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/0e25a5ef993c45a582df334ea2178db7.html "Converts a number from radians to degrees.") :arrow_upper_right:

