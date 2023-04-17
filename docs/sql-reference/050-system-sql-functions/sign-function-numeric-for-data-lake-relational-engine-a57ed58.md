<!-- loioa57ed58c84f21015bb5e803787dd27eb -->

# SIGN Function \[Numeric\] for Data Lake Relational Engine

Returns the sign of a number.



```
SIGN ( <numeric-expression> )
```



<a name="loioa57ed58c84f21015bb5e803787dd27eb__SIGN_parm1"/>

## Parameters

 *<numeric-expression\>*
 :   The number for which the sign is to be returned.

 

<a name="loioa57ed58c84f21015bb5e803787dd27eb__SIGN_returns1"/>

## Returns

SMALLINT



<a name="loioa57ed58c84f21015bb5e803787dd27eb__SIGN_remarks1"/>

## Remarks

`SIGN` returns the following:

-   \-1 – for negative numbers
-   0 – for zero
-   1 – for positie numbers



<a name="loioa57ed58c84f21015bb5e803787dd27eb__SIGN_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – compatible with SAP Adaptive Server Enterprise



<a name="loioa57ed58c84f21015bb5e803787dd27eb__SIGN_example1"/>

## Example

The following statement returns the value -1:

```
SELECT SIGN( -550 ) FROM iq_dummy
```

**Related Information**  


[SIGN Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/39dc72ab4eeb4d198cc7f4c051fa4b0d.html "Returns the sign of a number.") :arrow_upper_right:

