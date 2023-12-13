<!-- loio54d4912c1eb74fccac5ded7c6fc9fa8d -->

# YEAR Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns a 4-digit number corresponding to the year of the given date/time.



```
YEAR ( <timestamp-expression> );
```



<a name="loio54d4912c1eb74fccac5ded7c6fc9fa8d__section_tcw_wcv_vrb"/>

## Parameters


<dl>
<dt><b>

*<timestamp-expression\>*

</b></dt>
<dd>

A date and time.



</dd>
</dl>



<a name="loio54d4912c1eb74fccac5ded7c6fc9fa8d__section_ajb_1dv_vrb"/>

## Result Set

SMALLINT



<a name="loio54d4912c1eb74fccac5ded7c6fc9fa8d__section_vdp_1dv_vrb"/>

## Remarks

The `YEAR` function is the same as the `YEARS` \(*<timestamp-expression\>*\) function.



<a name="loio54d4912c1eb74fccac5ded7c6fc9fa8d__section_d44_lp3_wrb"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loio54d4912c1eb74fccac5ded7c6fc9fa8d__section_o45_bdv_vrb"/>

## Example

The following statement returns the value 1998:

```
SELECT YEAR( '1998-07-13 06:07:12' ) FROM iq_dummy;
```

**Related Information**  


[YEAR Function \[Date and Time\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a591eb9d84f210159e35a75b4b036a0d.html "Returns a 4-digit number corresponding to the year of the given date/time.") :arrow_upper_right:

