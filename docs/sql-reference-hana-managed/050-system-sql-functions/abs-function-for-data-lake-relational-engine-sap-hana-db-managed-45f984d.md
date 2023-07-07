<!-- loio45f984dcb7e440c4b082a7ef7662f923 -->

# ABS Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the absolute value of a numeric expression.



```
ABS ( <numeric-expression> )
```



<a name="loio45f984dcb7e440c4b082a7ef7662f923__section_u2t_51l_srb"/>

## Parameters


<dl>
<dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

The number that has the absolute value to be returned.



</dd>
</dl>



<a name="loio45f984dcb7e440c4b082a7ef7662f923__section_cdh_v1l_srb"/>

## Returns

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



<a name="loio45f984dcb7e440c4b082a7ef7662f923__section_m3y_v1l_srb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loio45f984dcb7e440c4b082a7ef7662f923__section_zs3_w1l_srb"/>

## Example

The following statement returns the value 66:

```
SELECT ABS( -66 ) FROM iq_dummy
```

**Related Information**  


[ABS Function [Numeric] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a532439384f21015be5cb176f7ecbae4.html "Returns the absolute value of a numeric expression.") :arrow_upper_right:

