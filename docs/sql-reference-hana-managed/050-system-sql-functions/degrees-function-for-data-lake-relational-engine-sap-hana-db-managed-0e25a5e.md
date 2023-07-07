<!-- loio0e25a5ef993c45a582df334ea2178db7 -->

# DEGREES Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Converts a number from radians to degrees.



```
DEGREES ( <numeric-expression> )
```



<a name="loio0e25a5ef993c45a582df334ea2178db7__section_vst_m1m_srb"/>

## Parameters


<dl>
<dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

An angle in radians.



</dd>
</dl>



<a name="loio0e25a5ef993c45a582df334ea2178db7__section_wzr_p1m_srb"/>

## Returns

Returns the degrees of the angle given by *<numeric-expression\>*.

DOUBLE



<a name="loio0e25a5ef993c45a582df334ea2178db7__section_frg_q1m_srb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loio0e25a5ef993c45a582df334ea2178db7__section_w5s_q1m_srb"/>

## Example

The following statement returns the value 29.793805:

```
SELECT DEGREES( 0.52 ) FROM iq_dummy
```

**Related Information**  


[DEGREES Function [Numeric] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a54c87d684f21015a9b9f518179a73ff.html "Converts a number from radians to degrees.") :arrow_upper_right:

