<!-- loioa566193184f2101587e8896021cbc6c7 -->

# MONTHNAME Function \[Date and Time\] for Data Lake Relational Engine

Returns the name of the month from the specified date expression.



```
MONTHNAME ( <date-expression> )
```



<a name="loioa566193184f2101587e8896021cbc6c7__MONTHNAME_parm1"/>

## Parameters

 *<date-expression\>*
 :   The datetime value.

 

<a name="loioa566193184f2101587e8896021cbc6c7__MONTHNAME_returns1"/>

## Returns

VARCHAR



<a name="loioa566193184f2101587e8896021cbc6c7__MONTHNAME_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa566193184f2101587e8896021cbc6c7__MONTHNAME_examples1"/>

## Example

The following statement returns the value September, when the DATE\_ORDER option is set to the default value of *<ymd\>*:

```
SELECT MONTHNAME( '1998-09-05' ) FROM iq_dummy
```

**Related Information**  


[MONTHNAME Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/2a2b0c17b30f48c296c26c8fb26c7ace.html "Returns the name of the month from the specified date expression.") :arrow_upper_right:

