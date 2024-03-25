<!-- loio57330a53cc29480ebf71c3bc97486052 -->

# QUARTER Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns a number indicating the quarter of the year from the supplied date expression.



```
QUARTER( <date-expression> );
```



<a name="loio57330a53cc29480ebf71c3bc97486052__section_xhf_wn5_vrb"/>

## Parameters


<dl>
<dt><b>

*<date-expression\>*

</b></dt>
<dd>

A date.



</dd>
</dl>



<a name="loio57330a53cc29480ebf71c3bc97486052__section_pjv_wn5_vrb"/>

## Result Set

INT



<a name="loio57330a53cc29480ebf71c3bc97486052__section_mwg_xn5_vrb"/>

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



<a name="loio57330a53cc29480ebf71c3bc97486052__section_dnw_xn5_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loio57330a53cc29480ebf71c3bc97486052__section_ykg_yn5_vrb"/>

## Example

With the `DATE_ORDER` option set to the default of *<ymd\>*, the following statement returns the value 2:

```
SELECT QUARTER ( '1987/05/02' ) FROM iq_dummy;
```

**Related Information**  


[QUARTER Function \[Date and Time\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a571b27b84f21015b649cee091ad3bd6.html "Returns a number indicating the quarter of the year from the supplied date expression.") :arrow_upper_right:

