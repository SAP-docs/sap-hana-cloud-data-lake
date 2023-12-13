<!-- loio3beacafc6c5f10148800a99aa1602905 -->

# SYSTEXTIDXTAB System View for Data Lake Relational Engine

Each row in the SYSTEXTIDXTAB system view describes a generated table that is part of a text index. The underlying system table for this view is ISYSTEXTIDXTAB.



<a name="loio3beacafc6c5f10148800a99aa1602905__section_i2m_qpq_b4b"/>

## Usage

This data lake Relational Engine system view can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




<table>
<tr>
<th valign="top">

Column name

</th>
<th valign="top">

Data type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

index\_id

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

For internal use only.

</td>
</tr>
<tr>
<td valign="top">

sequence

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

For internal use only.

</td>
</tr>
<tr>
<td valign="top">

table\_type

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

For internal use only.

</td>
</tr>
<tr>
<td valign="top">

table\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

For internal use only.

</td>
</tr>
</table>

