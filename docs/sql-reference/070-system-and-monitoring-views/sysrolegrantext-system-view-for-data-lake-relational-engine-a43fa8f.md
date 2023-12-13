<!-- loioa43fa8fb84f21015a0c69a92f5590bc6 -->

# SYSROLEGRANTEXT System View for Data Lake Relational Engine

The SYSROLEGRANTEXT system view contains syntax extensions pertaining to the SET USER and CHANGE PASSWORD system privilege and is related to the SYSROLEGRANT system view.



<a name="loioa43fa8fb84f21015a0c69a92f5590bc6__section_v1w_qbq_b4b"/>

## Usage

This data lake Relational Engine system view can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.


<table>
<tr>
<th valign="top">

Column Name

</th>
<th valign="top">

Data Type

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

ID used to identify each GRANT statement.

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

The user\_ids specified in `user-list` or `role-list` in a particular extended grant.

</td>
</tr>
</table>



## Remarks

When you grant or revoke the SET USER or CHANGE PASSWORD privilege, either with the user-list option or with ANY WITH ROLES role-list option, this view is updated with the values from the extended syntax.



## Constraints on Underlying System Table

```
PRIMARY KEY (grant_id, user_id);
```

