<!-- loioff2ca422e5af48f58bd55ec839860dd4 -->

# SECOND Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns a number from 0 to 59 corresponding to the second component of the given date/time value.



```
SECOND ( <datetime-expression> )
```



<a name="loioff2ca422e5af48f58bd55ec839860dd4__section_kg4_yz5_vrb"/>

## Parameters


<dl>
<dt><b>

*<datetime-expression\>*

</b></dt>
<dd>

The date and time value.



</dd>
</dl>



<a name="loioff2ca422e5af48f58bd55ec839860dd4__section_slc_zz5_vrb"/>

## Returns

SMALLINT



<a name="loioff2ca422e5af48f58bd55ec839860dd4__section_d1m_zz5_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – compatible with SAP Adaptive Server Enterprise



<a name="loioff2ca422e5af48f58bd55ec839860dd4__section_gw2_11v_vrb"/>

## Example

The following statement returns the value 5:

```
SELECT SECOND( '1998-07-13 08:21:05' ) FROM iq_dummy
```

**Related Information**  


[SECOND Function [Date and Time] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a57dc03b84f210158836c9258c67e700.html "Returns a number from 0 to 59 corresponding to the second component of the given date/time value.") :arrow_upper_right:

