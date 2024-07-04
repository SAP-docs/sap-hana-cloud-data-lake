<!-- loioa571b27b84f21015b649cee091ad3bd6 -->

# QUARTER Function \[Date and Time\] for Data Lake Relational Engine

Returns a number indicating the quarter of the year from the supplied date expression.



```
QUARTER( <date-expression> );
```



<a name="loioa571b27b84f21015b649cee091ad3bd6__QUARTER_parm1"/>

## Parameters


<dl>
<dt><b>

*<date-expression\>*

</b></dt>
<dd>

A date.



</dd>
</dl>



<a name="loioa571b27b84f21015b649cee091ad3bd6__QUARTER_returns1"/>

## Result Set

INT



<a name="loioa571b27b84f21015b649cee091ad3bd6__QUARTER_remarks1"/>

## Remarks

This table lists the dates in the quarters of the year. Function assumes as starting quarter of 1 \(January\). For a user-defined starting quarter, use `QUARTERSTR`.


<table>
<tr>
<th valign="top" rowspan="1">

Quarter

</th>
<th valign="top" rowspan="1">

Period \(Inclusive\)

</th>
</tr>
<tr>
<td valign="top" rowspan="1">

1

</td>
<td valign="top" rowspan="1">

January 1 to March 31

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

2

</td>
<td valign="top" rowspan="1">

April 1 to June 30

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

3

</td>
<td valign="top" rowspan="1">

July 1 to September 30

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

4

</td>
<td valign="top" rowspan="1">

October 1 to December 31

</td>
</tr>
</table>



<a name="loioa571b27b84f21015b649cee091ad3bd6__QUARTER_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioa571b27b84f21015b649cee091ad3bd6__QUARTER_example1"/>

## Examples

With the `DATE_ORDER` option set to the default of *<ymd\>*, the following statement returns the value 2:

```
SELECT QUARTER ( '1987/05/02' ) FROM iq_dummy;
```

**Related Information**  


[QUARTERSTR Function \[Date and Time\] for Data Lake Relational Engine](quarterstr-function-date-and-time-for-data-lake-relational-engine-8fbd6b7.md "Returns a number indicating the quarter of the year from the supplied date expression and quarter start month.")

[QUARTER Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/57330a53cc29480ebf71c3bc97486052.html "Returns a number indicating the quarter of the year from the supplied date expression.") :arrow_upper_right:

