<!-- loio8081001d5f8e4323a5f13cc57fb91cf1 -->

# ATAN2 Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the arc-tangent, in radians, of the ratio of two numbers.



```
ATAN2 ( <numeric-expression1>, <numeric-expression2> )
```



<a name="loio8081001d5f8e4323a5f13cc57fb91cf1__section_wck_m3k_srb"/>

## Parameters

 *<numeric-expression1\>*
 :   The numerator in the ratio whose arc tangent is calculated.

  *<numeric-expression2\>*
 :   The denominator in the ratio whose arc-tangent is calculated.

 

<a name="loio8081001d5f8e4323a5f13cc57fb91cf1__section_ltv_m3k_srb"/>

## Returns

DOUBLE



<a name="loio8081001d5f8e4323a5f13cc57fb91cf1__section_wyj_n3k_srb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loio8081001d5f8e4323a5f13cc57fb91cf1__section_l2w_n3k_srb"/>

## Example

The following statement returns the value 0.00866644968879073143:

```
SELECT ATAN2( 0.52, 060 ) FROM iq_dummy
```

**Related Information**  


[ATAN2 Function [Numeric] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a5356c1b84f210159f68d03274510fe6.html "Returns the arc-tangent, in radians, of the ratio of two numbers.") :arrow_upper_right:

