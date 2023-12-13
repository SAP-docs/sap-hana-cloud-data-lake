<!-- loioa43fd7c284f21015a2949dd1bb7ef367 -->

# SYSROLEGRANTS System View for Data Lake Relational Engine

The SYSROLEGRANTS system view is the same as the SYSROLEGRANT system view but includes two additional columns: the name of the role \(not just the role ID\) and the name of the grantee \(not just user ID\).



<a name="loioa43fd7c284f21015a2949dd1bb7ef367__section_v1w_qbq_b4b"/>

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

grant\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

A unique identifier for each grant statement issued.

</td>
</tr>
<tr>
<td valign="top">

role\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The unique identifier for the role granted to a user \(as defined in the `ISYSUSER` table\).

</td>
</tr>
<tr>
<td valign="top">

role\_name

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

The name of the role corresponding to the role\_id value.

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

The unique identifier for the user granted the role.

</td>
</tr>
<tr>
<td valign="top">

grantee\_name

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

The name of the grantee corresponding to the grantee value.

</td>
</tr>
<tr>
<td valign="top">

grant\_type

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

Identifies how the role and its underlying privileges were granted. Values:

-   1 – Underlying privileges are granted with no administrative rights and no privilege inheritance.
-   3 – Underlying privileges are granted with administrative rights, but with no privilege inheritance.
-   5 – Underlying privileges are granted with no administrative rights, but with privilege inheritance.
-   6 – Only administrative rights to the underlying privileges are granted.
-   7 – Underlying privileges are granted with administrative rights and privilege inheritance.



</td>
</tr>
<tr>
<td valign="top">

grant\_scope

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

Defines the range to which the grant applies. Values include:

-   1 – User list
-   2 – Any users granted membership in the specified roles
-   3 – All users

> ### Note:  
> This value is applicable to the SET USER and CHANGE PASSWORD system privileges only and can store any valid combination of these values.



</td>
</tr>
<tr>
<td valign="top">

grantor

</td>
<td valign="top">

CHAR \(128\)

</td>
<td valign="top">

The unique identifier of the grantor of the role.

</td>
</tr>
</table>

