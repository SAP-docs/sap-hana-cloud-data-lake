<!-- loioa565928184f21015aecd84c01c4c2078 -->

# MONTH Function \[Date and Time\] for Data Lake Relational Engine

Returns a number from 1 to 12 corresponding to the month of the given date.



```
MONTH ( <date-expression> );
```



<a name="loioa565928184f21015aecd84c01c4c2078__MONTH_parm1"/>

## Parameters


<dl>
<dt><b>

*<date-expression\>*

</b></dt>
<dd>

A date/time value.



</dd>
</dl>



<a name="loioa565928184f21015aecd84c01c4c2078__MONTH_returns1"/>

## Result Set

SMALLINT



<a name="loioa565928184f21015aecd84c01c4c2078__MONTH_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa565928184f21015aecd84c01c4c2078__MONTH_examples"/>

## Examples

The following statement returns the value 7:

```
SELECT MONTH( '1998-07-13' ) FROM iq_dummy;
```

**Related Information**  


[MONTH Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/63319ccc3d6847fab168f3418d0fec07.html "Returns a number from 1 to 12 corresponding to the month of the given date.") :arrow_upper_right:

