<!-- loio3be7eb936c5f1014b178fa1858412565 -->

# SYSDBSPACEPERM System View for Data Lake Relational Engine

Each row in the SYSDBSPACEPERM system view describes a privilege on a dbspace file. The underlying system table for this view is ISYSDBSPACEPERM.



<a name="loio3be7eb936c5f1014b178fa1858412565__section_v1w_qbq_b4b"/>

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

dbspace\_id

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Unique number identifying the dbspace. The system dbspace contains all system objects and has a dbspace\_id of 0.

</td>
</tr>
<tr>
<td valign="top">

grantee

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The user ID of the user getting the privilege.

</td>
</tr>
<tr>
<td valign="top">

privilege\_type

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

The privilege that is granted to the grantee. For example, CREATE gives the grantee privilege to create objects on the dbspace.

</td>
</tr>
</table>

