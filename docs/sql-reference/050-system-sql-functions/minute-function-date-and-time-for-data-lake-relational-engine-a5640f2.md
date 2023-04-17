<!-- loioa5640f2284f21015825db935889f60d9 -->

# MINUTE Function \[Date and Time\] for Data Lake Relational Engine

Returns a number from 0 to 59 corresponding to the minute component of the specified date/time value.



```
MINUTE ( <datetime-expression> )
```



<a name="loioa5640f2284f21015825db935889f60d9__MINUTE_parm1"/>

## Parameters

 *<datetime-expression\>*
 :   The date/time value.

 

<a name="loioa5640f2284f21015825db935889f60d9__MINUTE_returns1"/>

## Returns

SMALLINT



<a name="loioa5640f2284f21015825db935889f60d9__MINUTE_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa5640f2284f21015825db935889f60d9__MINUTE_examples1"/>

## Example

The following statement returns the value 22:

```
SELECT MINUTE( '1998-07-13 12:22:34' ) FROM iq_dummy
```

**Related Information**  


[MINUTE Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/4b1c8e2d8caa4878ac564dcdc0ffacea.html "Returns a number from 0 to 59 corresponding to the minute component of the specified date/time value.") :arrow_upper_right:

