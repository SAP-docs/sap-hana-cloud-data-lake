<!-- loioa532439384f21015be5cb176f7ecbae4 -->

# ABS Function \[Numeric\] for Data Lake Relational Engine

Returns the absolute value of a numeric expression.



```
ABS ( <numeric-expression> );
```



<a name="loioa532439384f21015be5cb176f7ecbae4__ABS_parm1"/>

## Parameters


<dl>
<dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

The number that has the absolute value to be returned.



</dd>
</dl>



<a name="loioa532439384f21015be5cb176f7ecbae4__ABS_returns1"/>

## Result Set

An absolute value of the numeric expression.


<table>
<tr>
<th valign="top">

Numeric Expression Data Type

</th>
<th valign="top">

Returns

</th>
</tr>
<tr>
<td valign="top">

INT

</td>
<td valign="top">

INT

</td>
</tr>
<tr>
<td valign="top">

FLOAT

</td>
<td valign="top">

FLOAT

</td>
</tr>
<tr>
<td valign="top">

DOUBLE

</td>
<td valign="top">

DOUBLE

</td>
</tr>
<tr>
<td valign="top">

NUMERIC

</td>
<td valign="top">

NUMERIC

</td>
</tr>
</table>



<a name="loioa532439384f21015be5cb176f7ecbae4__ABS_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa532439384f21015be5cb176f7ecbae4__ABS_examples1"/>

## Example

The following statement returns the value 66:

```
SELECT ABS( -66 ) FROM iq_dummy;
```

**Related Information**  


[ABS Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/45f984dcb7e440c4b082a7ef7662f923.html "Returns the absolute value of a numeric expression.") :arrow_upper_right:

