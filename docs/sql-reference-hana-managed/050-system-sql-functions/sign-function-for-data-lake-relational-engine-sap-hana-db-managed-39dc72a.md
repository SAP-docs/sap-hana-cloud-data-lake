<!-- loio39dc72ab4eeb4d198cc7f4c051fa4b0d -->

# SIGN Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the sign of a number.



```
SIGN ( <numeric-expression> )
```



<a name="loio39dc72ab4eeb4d198cc7f4c051fa4b0d__section_r35_2z5_vrb"/>

## Parameters


<dl>
<dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

The number for which the sign is to be returned.



</dd>
</dl>



<a name="loio39dc72ab4eeb4d198cc7f4c051fa4b0d__section_hdb_l43_wrb"/>

## Returns

SMALLINT



<a name="loio39dc72ab4eeb4d198cc7f4c051fa4b0d__section_cvv_fz5_vrb"/>

## Remarks

`SIGN` returns the following:

-   \-1 – for negative numbers
-   0 – for zero
-   1 – for positie numbers



<a name="loio39dc72ab4eeb4d198cc7f4c051fa4b0d__section_nlk_gz5_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – compatible with SAP Adaptive Server Enterprise



<a name="loio39dc72ab4eeb4d198cc7f4c051fa4b0d__section_fb5_gz5_vrb"/>

## Example

The following statement returns the value -1:

```
SELECT SIGN( -550 ) FROM iq_dummy
```

**Related Information**  


[SIGN Function [Numeric] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a57ed58c84f21015bb5e803787dd27eb.html "Returns the sign of a number.") :arrow_upper_right:

