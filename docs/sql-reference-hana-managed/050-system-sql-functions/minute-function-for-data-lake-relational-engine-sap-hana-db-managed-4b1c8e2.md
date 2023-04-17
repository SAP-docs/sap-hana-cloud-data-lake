<!-- loio4b1c8e2d8caa4878ac564dcdc0ffacea -->

# MINUTE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns a number from 0 to 59 corresponding to the minute component of the specified date/time value.



```
MINUTE ( <datetime-expression> )
```



<a name="loio4b1c8e2d8caa4878ac564dcdc0ffacea__section_olr_tgn_vrb"/>

## Parameters

 *<datetime-expression\>*
 :   The date/time value.

 

<a name="loio4b1c8e2d8caa4878ac564dcdc0ffacea__section_zkb_5gn_vrb"/>

## Returns

SMALLINT



<a name="loio4b1c8e2d8caa4878ac564dcdc0ffacea__section_mdt_5gn_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loio4b1c8e2d8caa4878ac564dcdc0ffacea__section_tsb_vgn_vrb"/>

## Example

The following statement returns the value 22:

```
SELECT MINUTE( '1998-07-13 12:22:34' ) FROM iq_dummy
```

**Related Information**  


[MINUTE Function [Date and Time] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a5640f2284f21015825db935889f60d9.html "Returns a number from 0 to 59 corresponding to the minute component of the specified date/time value.") :arrow_upper_right:

