<!-- loio8c15112761fa4dba8aa2d0cb3a89db92 -->

# sp\_displayroles System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Displays all roles granted to a user-defined role or a user, or displays the entire hierarchical tree of roles.



<a name="loio8c15112761fa4dba8aa2d0cb3a89db92__section_dh4_3db_1yb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.

> ### Restriction:  
> This syntax cannot be run when connected to SAP HANA database as a SAP HANA database user and using SAP HANA database REMOTE\_EXECUTE or REMOTE\_EXECUTE\_QUERY.



```
sp_displayroles( [ <user_role_name>[, <display_mode> 
   [, <grant_type> ] ] ] )
```



<a name="loio8c15112761fa4dba8aa2d0cb3a89db92__section_pyq_cc2_srb"/>

## Parameters


<dl>
<dt><b>

*<user\_role\_name\>*

</b></dt>
<dd>

The user role name. Valid values are:

-   A valid system privilege name or system privilege role name
-   A valid user-defined role name
-   A valid user name

By default, if no argument is specified, the current login user is used.



</dd><dt><b>

*<display\_mode\>*

</b></dt>
<dd>

The display mode. Valid values are:

-   EXPAND\_UP – shows all roles granted the input role or system privilege; that is the role hierarchy tree for the parent levels.
-   EXPAND\_DOWN – shows all roles or system privileges granted to the input role or user; that is, the role hierarchy tree for the child levels.

If no argument is specified \(default\), only the directly granted roles or system privileges appear.



</dd><dt><b>

*<grant\_type\>*

</b></dt>
<dd>

The grant type. Valid values are:

-   ALL – shows all roles or system privileges granted.
-   NO\_ADMIN – shows all roles or system privileges granted with the WITH NO ADMIN OPTION or WITH ADMIN OPTION clause.
-   ADMIN – shows all roles or system privileges granted with the WITH ADMIN OPTION or WITH ADMIN ONLY OPTION clause.

If no argument is specified, `ALL` is used.



</dd>
</dl>



<a name="loio8c15112761fa4dba8aa2d0cb3a89db92__section_ik3_dc2_srb"/>

## Result Set


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

`role_name`

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

Lists role/system privilege name.

</td>
</tr>
<tr>
<td valign="top">

`parent_role_name`

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

Lists role name of the parent.

</td>
</tr>
<tr>
<td valign="top">

`grant_type`

</td>
<td valign="top">

CHAR\(10\)

</td>
<td valign="top">

Lists grant type.

</td>
</tr>
<tr>
<td valign="top">

`role_level`

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

For `Expand_down` mode, 1 indicates directly granted roles; 2 indicates the next hierarchy below, and so on. For `Expand_up` mode, 0 indicates the roles to which the specified role is granted; -1 indicates the next hierarchy above, and so on.

</td>
</tr>
</table>



<a name="loio8c15112761fa4dba8aa2d0cb3a89db92__section_jvz_dc2_srb"/>

## Remarks

For:

-   Name = System privilege name – the results show the system privilege name instead of the system privilege role name.
-   Mode = Expand\_down – parent\_role\_name is NULL for level 1 \(directly granted roles\). If no mode is specified \(default\), role\_level is 1 and parent\_role\_name is NULL, since only directly granted roles appear.
-   Name = User name, with Mode = expand\_up – no results are returned since a user resides at the top level in any role hierarchy. Similarly, if Name = an immutable system privilege name, with Mode = Expand\_down, no results are returned because an immutable system privilege resides at the bottom level in any role hierarchy.
-   Default Mode – parent\_role\_name column is NULL and role\_level is 1.



<a name="loio8c15112761fa4dba8aa2d0cb3a89db92__section_z5w_tw1_1yb"/>

## Privileges



### 

Requires EXECUTE object-level privilege on the procedure. To return the system privileges or roles for another user ID or a role, also require the MANAGE ROLES system privilege.



<a name="loio8c15112761fa4dba8aa2d0cb3a89db92__section_fhr_2c2_srb"/>

## Side Effects

None



<a name="loio8c15112761fa4dba8aa2d0cb3a89db92__section_c5m_hc2_srb"/>

## Examples

This example uses sp\_displayroles to return all roles or system privileges granted to USER1:

```
CALL sp_displayroles( 'USER1', 'EXPAND_DOWN', 'ALL' );
```


<table>
<tr>
<th valign="top">

role\_name

</th>
<th valign="top">

parent\_role\_name

</th>
<th valign="top">

grant\_type

</th>
<th valign="top">

role\_level

</th>
</tr>
<tr>
<td valign="top">

PUBLIC

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NO ADMIN

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

MONITOR

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NO ADMIN

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

CREATE ANY OBJECT

</td>
<td valign="top">

NULL

</td>
<td valign="top">

ADMIN ONLY

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

NEW\_CONNECTIONS\_ROLE

</td>
<td valign="top">

NULL

</td>
<td valign="top">

ADMIN

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

SYS\_DL\_CUSTOMER\_ROLE

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NO ADMIN

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

NEW\_USER\_COCKPIT\_ROLE

</td>
<td valign="top">

NULL

</td>
<td valign="top">

ADMIN

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

SET ANY CUSTOMER PUBLIC OPTION

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NO ADMIN

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

READ FILE

</td>
<td valign="top">

NEW\_CONNECTIONS\_ROLE

</td>
<td valign="top">

NO ADMIN

</td>
<td valign="top">

2

</td>
</tr>
<tr>
<td valign="top">

SET ANY CUSTOMER PUBLIC OPTION

</td>
<td valign="top">

NEW\_CONNECTIONS\_ROLE

</td>
<td valign="top">

NO ADMIN

</td>
<td valign="top">

2

</td>
</tr>
</table>

**Related Information**  


[sp_displayroles System Procedure for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a44ba32684f2101598cba97bb3b1b4d4.html "Displays all roles granted to a user-defined role or a user, or displays the entire hierarchical tree of roles.") :arrow_upper_right:

