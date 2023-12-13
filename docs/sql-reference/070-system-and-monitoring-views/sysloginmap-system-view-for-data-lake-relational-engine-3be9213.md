<!-- loio3be9213a6c5f1014a2c28ce5dc6c41c8 -->

# SYSLOGINMAP System View for Data Lake Relational Engine

The SYSLOGINMAP system view contains one row for each user that can connect to the database using either an integrated login, or Kerberos login. For that reason, access to this view is restricted. The underlying system table for this view is ISYSLOGINMAP.



<a name="loio3be9213a6c5f1014a2c28ce5dc6c41c8__section_v1w_qbq_b4b"/>

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

login\_mode

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

The type of login: 1 for integrated logins, 2 for Kerberos logins.

</td>
</tr>
<tr>
<td valign="top">

login\_id

</td>
<td valign="top">

VARCHAR\(1024\)

</td>
<td valign="top">

Either the integrated login user profile name, or the Kerberos principal that maps to database\_uid.

</td>
</tr>
<tr>
<td valign="top">

object\_id

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

A unique identifier, one for each mapping between user ID and database user ID.

</td>
</tr>
<tr>
<td valign="top">

database\_uid

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The database user ID to which the login ID is mapped.

</td>
</tr>
</table>

