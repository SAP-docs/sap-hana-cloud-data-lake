<!-- loio3beae1036c5f1014bf17fc2cb4c22fed -->

# SYSTYPEMAP System View for Data Lake Relational Engine

The SYSTYPEMAP system view contains the compatibility mapping values for entries in the SYSSQLSERVERTYPE system view. The underlying system table for this view is ISYSTYPEMAP.



<a name="loio3beae1036c5f1014bf17fc2cb4c22fed__section_v1w_qbq_b4b"/>

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

ss\_user\_type

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Contains the Adaptive Server Enterprise user type.

</td>
</tr>
<tr>
<td valign="top">

sa\_domain\_id

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Contains the corresponding data lake Relational Engine domain\_id.

</td>
</tr>
<tr>
<td valign="top">

sa\_user\_type

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Contains the corresponding data lake Relational Engine user type.

</td>
</tr>
<tr>
<td valign="top">

nullable

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

Whether the type allows NULL values.

</td>
</tr>
</table>

