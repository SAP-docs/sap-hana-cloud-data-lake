<!-- loio3be8c0876c5f101486b0cb0a735c7573 -->

# SYSGROUP Compatibility View for Data Lake Relational Engine

There is one row in the SYSGROUP system view for each member of each group. This view describes the many-to-many relationship between groups and members. A group may have many members, and a user may be a member of many groups.



<a name="loio3be8c0876c5f101486b0cb0a735c7573__section_v1w_qbq_b4b"/>

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

group\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The user number of the group.

</td>
</tr>
<tr>
<td valign="top">

group\_member

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The user number of a member.

</td>
</tr>
</table>

