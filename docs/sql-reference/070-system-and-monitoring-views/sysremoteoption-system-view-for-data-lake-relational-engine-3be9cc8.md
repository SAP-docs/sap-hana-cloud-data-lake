<!-- loio3be9cc816c5f1014892df503c93c8381 -->

# SYSREMOTEOPTION System View for Data Lake Relational Engine

Each row in the SYSREMOTEOPTION system view describes the value of a message link parameter. The underlying system table for this view is ISYSREMOTEOPTION.



<a name="loio3be9cc816c5f1014892df503c93c8381__section_v1w_qbq_b4b"/>

## Usage

This data lake Relational Engine system view can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



Some columns in this view contain potentially sensitive data. The SYSREMOTEOPTION2 view provides public access to the data in this view except for the potentially sensitive columns.


<table>
<tr>
<th valign="top">

Column

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

option\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

An identification number for the message link parameter.

</td>
</tr>
<tr>
<td valign="top">

user\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The user ID for which the parameter is set.

</td>
</tr>
<tr>
<td valign="top">

setting

</td>
<td valign="top">

VARCHAR\(255\)

</td>
<td valign="top">

The value of the message link parameter.

</td>
</tr>
</table>

