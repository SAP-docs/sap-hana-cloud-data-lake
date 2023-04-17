<!-- loio2a2b0c17b30f48c296c26c8fb26c7ace -->

# MONTHNAME Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the name of the month from the specified date expression.



```
MONTHNAME ( <date-expression> )
```



<a name="loio2a2b0c17b30f48c296c26c8fb26c7ace__section_nbr_w2n_vrb"/>

## Parameters

 *<date-expression\>*
 :   The datetime value.

 

<a name="loio2a2b0c17b30f48c296c26c8fb26c7ace__section_tk4_x2n_vrb"/>

## Returns

VARCHAR



<a name="loio2a2b0c17b30f48c296c26c8fb26c7ace__section_ary_x2n_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loio2a2b0c17b30f48c296c26c8fb26c7ace__section_gyn_y2n_vrb"/>

## Example

The following statement returns the value September, when the DATE\_ORDER option is set to the default value of *<ymd\>*:

```
SELECT MONTHNAME( '1998-09-05' ) FROM iq_dummy
```

**Related Information**  


[MONTHNAME Function [Date and Time] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a566193184f2101587e8896021cbc6c7.html "Returns the name of the month from the specified date expression.") :arrow_upper_right:

