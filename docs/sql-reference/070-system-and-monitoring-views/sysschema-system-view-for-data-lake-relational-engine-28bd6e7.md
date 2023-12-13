<!-- loio28bd6e7af3a74d36bd39680341f1b5f5 -->

# SYSSCHEMA System View for Data Lake Relational Engine

The SYSSCHEMA system view that displays a list of schemas.



<a name="loio28bd6e7af3a74d36bd39680341f1b5f5__section_v1w_qbq_b4b"/>

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

schema\_name

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

Displays the name of the schema.

</td>
</tr>
<tr>
<td valign="top">

schema\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

Displays the unique identifier for the schema.

</td>
</tr>
<tr>
<td valign="top">

owner\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

Displays the owner of the schema.

</td>
</tr>
</table>



<a name="loio28bd6e7af3a74d36bd39680341f1b5f5__section_xlz_2q1_m5b"/>

## Additional Information

Requires the SELECT ANY TABLE system privilege to display all schemas. Otherwise, only schemas owned by the current user or to which the current user has been granted any of the object-level privilege on the schema are displayed.

