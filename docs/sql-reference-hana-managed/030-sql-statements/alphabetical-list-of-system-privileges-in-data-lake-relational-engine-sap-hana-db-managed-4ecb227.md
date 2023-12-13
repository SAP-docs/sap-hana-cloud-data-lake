<!-- loio4ecb227108a6427cb9eb7b0903719aa2 -->

# Alphabetical List of System Privileges in Data Lake Relational Engine \(SAP HANA DB-Managed\)

A list of available system privileges.



System privileges control the rights of users to perform authorized database tasks.



> ### Note:  
> The system privileges available in Data Lake Relational Engine \(SAP HANA DB-Managed\) are a subset of those available in data lake Relational Engine. Only those privileges available to perform SQL tasks when directly connected to data lake Relational Engine within the context of a Data Lake Relational Engine \(SAP HANA DB-Managed\) instance are listed. For example, you can create a user-defined procedure or function when directly connected. Therefore, the procedure specific privileges are available. To create a table you must use the REMOTE\_EXECUTE procedure. Therefore, the privileges to create a table are not available.


<table>
<tr>
<th valign="top">

System Privilege

</th>
<th valign="top">

Allows a User To...

</th>
</tr>
<tr>
<td valign="top">

ALTER ANY OBJECT

</td>
<td valign="top">

Alter and comment on the following types of objects owned by any user:

-   Functions
-   Procedures



</td>
</tr>
<tr>
<td valign="top">

ALTER ANY PROCEDURE

</td>
<td valign="top">

Alter and comment on procedures and functions owned by any user.

</td>
</tr>
<tr>
<td valign="top">

CREATE ANY OBJECT

</td>
<td valign="top">

Create and comment on the following types of objects owned by any user:

-   Functions
-   Procedures



</td>
</tr>
<tr>
<td valign="top">

CREATE ANY PROCEDURE

</td>
<td valign="top">

Create and comment on procedures and functions owned by any user.

</td>
</tr>
<tr>
<td valign="top">

CREATE PROCEDURE

</td>
<td valign="top">

Create and comment on self-owned procedures and functions.

</td>
</tr>
<tr>
<td valign="top">

DROP ANY OBJECT

</td>
<td valign="top">

Drop the following types of objects owned by any user:

-   Functions
-   Procedures



</td>
</tr>
<tr>
<td valign="top">

DROP ANY PROCEDURE

</td>
<td valign="top">

Drop procedures and functions owned by any user.

</td>
</tr>
<tr>
<td valign="top">

MANAGE ANY OBJECT PRIVILEGE

</td>
<td valign="top">

Grant object privileges to users and roles.

</td>
</tr>
<tr>
<td valign="top">

MANAGE ANY TRACE SESSION

</td>
<td valign="top">

Create a trace session.

</td>
</tr>
<tr>
<td valign="top">

MANAGE ROLES

</td>
<td valign="top">

Grant roles to users and other roles.

</td>
</tr>
</table>

