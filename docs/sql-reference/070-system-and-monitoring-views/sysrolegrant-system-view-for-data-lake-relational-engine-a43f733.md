<!-- loioa43f733b84f2101594aed5bfe3904358 -->

# SYSROLEGRANT System View for Data Lake Relational Engine

The SYSROLEGRANT system view contains one row for each grant of a system or user defined role. The underlying system table for this view is ISYSROLEGRANT.



> ### Restriction:  
> This data lake Relational Engine system view can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




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

role\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

ID of the role being granted, as per ISYSUSER.



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

ID of the user being granted the role, as per ISYSUSER.



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

Describes type of grant using three digits. The first digit is whether privilege has been granted. The second digit is whether administration rights have been given. The third digit is whether system privileges are inheritable.

-   001 – privilege granted, with no inheritance, and no administration rights.
-   101 – privilege granted, with inheritance, but no administration rights.
-   110 – only administration rights have been granted.
-   111 – privilege granted, with inheritance, and with administration rights
-   001 – privilege granted, with administration rights, but no inheritance.



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

Used by SET USER and CHANGE PASSWORD to set the scope of the grant. Values can be one or more of the following:

-   001 – user list.
-   101 – ANY WITH ROLES.
-   110 – ANY.



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



## Constraints on Underlying System Table

```
PRIMARY KEY (grant_ID)
```

```
UNIQUE Index (role_id, grantee, grant_scope)
```

