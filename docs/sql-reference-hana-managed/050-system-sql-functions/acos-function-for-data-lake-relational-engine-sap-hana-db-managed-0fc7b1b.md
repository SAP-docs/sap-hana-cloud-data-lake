<!-- loio0fc7b1b85c8d4b6280000fc7e92152ee -->

# ACOS Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the arc-cosine, in radians, of a numeric expression.



```
ACOS ( <numeric-expression> )
```



<a name="loio0fc7b1b85c8d4b6280000fc7e92152ee__section_e52_k1l_srb"/>

## Parameters

 *<numeric-expression\>*
 :   The cosine of the angle.

 

<a name="loio0fc7b1b85c8d4b6280000fc7e92152ee__section_dcr_k1l_srb"/>

## Returns

DOUBLE



<a name="loio0fc7b1b85c8d4b6280000fc7e92152ee__section_jtc_l1l_srb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loio0fc7b1b85c8d4b6280000fc7e92152ee__section_jqq_l1l_srb"/>

## Example

The following statement returns the value 1.023945:

```
SELECT ACOS( 0.52 ) FROM iq_dummy
```

**Related Information**  


[ACOS Function [Numeric] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a532c20484f21015a4a5f8c26e3af9c7.html "Returns the arc-cosine, in radians, of a numeric expression.") :arrow_upper_right:

