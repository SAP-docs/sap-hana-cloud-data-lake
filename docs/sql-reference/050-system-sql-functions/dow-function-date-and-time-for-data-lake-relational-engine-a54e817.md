<!-- loioa54e817784f21015bfbbc50ea9eaecba -->

# DOW Function \[Date and Time\] for Data Lake Relational Engine

Returns a number from 1 to 7 representing the day of the week of the specified date, with Sunday=1, Monday=2, and so on.



```
DOW ( <date-expression> );
```



<a name="loioa54e817784f21015bfbbc50ea9eaecba__DOW_parm1"/>

## Parameters


<dl>
<dt><b>

*<date-expression\>*

</b></dt>
<dd>

The date.



</dd>
</dl>



<a name="loioa54e817784f21015bfbbc50ea9eaecba__DOW_returns1"/>

## Result Set

SMALLINT



<a name="loioa54e817784f21015bfbbc50ea9eaecba__DOW_remarks1"/>

## Remarks

Use the DATE\_FIRST\_DAY\_OF\_WEEK option if you need Monday \(or another day\) to be the first day of the week.



<a name="loioa54e817784f21015bfbbc50ea9eaecba__DOW_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa54e817784f21015bfbbc50ea9eaecba__DOW_eample1"/>

## Example

The following statement returns the value 5:

```
SELECT DOW( '1998-07-09' ) FROM iq_dummy;
```

**Related Information**  


[DOW Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/aae6da55cdb5426d9b6a06e2c7e5b2b4.html "Returns a number from 1 to 7 representing the day of the week of the specified date, with Sunday=1, Monday=2, and so on.") :arrow_upper_right:

