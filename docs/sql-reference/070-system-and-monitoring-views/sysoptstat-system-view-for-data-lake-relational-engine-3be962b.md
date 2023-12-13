<!-- loio3be962b56c5f10148abcef42e20b1126 -->

# SYSOPTSTAT System View for Data Lake Relational Engine

The SYSOPTSTAT system view stores the cost model calibration information as computed by the ALTER DATABASE CALIBRATE statement. The contents of this view are for internal use only and are best accessed via the sa\_get\_dtt system procedure. The underlying system table for this view is ISYSOPTSTAT.



<a name="loio3be962b56c5f10148abcef42e20b1126__section_v1w_qbq_b4b"/>

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

stat\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

For system use only.

</td>
</tr>
<tr>
<td valign="top">

group\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

For system use only.

</td>
</tr>
<tr>
<td valign="top">

format\_id

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

For system use only.

</td>
</tr>
<tr>
<td valign="top">

data

</td>
<td valign="top">

LONG BINARY

</td>
<td valign="top">

For system use only.

</td>
</tr>
</table>

