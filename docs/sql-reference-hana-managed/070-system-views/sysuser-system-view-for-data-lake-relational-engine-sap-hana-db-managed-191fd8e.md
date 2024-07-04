<!-- loio191fd8e1a9594171a03df906f59e0a4f -->

# SYSUSER System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Each row in the SYS.SYSUSER system view describes a user, role, or schema in the system.



## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system view can be used when connected as follows:

-   Connected to SAP HANA database as a SAP HANA database user, and using SAP HANA database REMOTE\_EXECUTE\_QUERY.





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

user\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

A unique identifier for the user assigned to the login policy.

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

A unique identifier for the user in the database.

</td>
</tr>
<tr>
<td valign="top">

user\_name

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

The login name for the user.

</td>
</tr>
<tr>
<td valign="top">

password

</td>
<td valign="top">

CHAR\(3\)

</td>
<td valign="top">

Whether a password is stored. Three asterisks \(\*\*\*\) indicate that a password is stored. NULL indicates that no password is stored. You can return actual password hash values by querying the SYS.SYSUSERPASSWORD system view.

</td>
</tr>
<tr>
<td valign="top">

login\_policy\_id

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

A unique identifier for the login policy.

</td>
</tr>
<tr>
<td valign="top">

expire\_password\_on\_login

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

A value that indicates if the password for the user expires at the next login.

</td>
</tr>
<tr>
<td valign="top">

password\_creation\_time

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

The local time that the password was created for the user.

</td>
</tr>
<tr>
<td valign="top">

failed\_login\_attempts

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The number of times that a user can fail to log in before the account is locked.

</td>
</tr>
<tr>
<td valign="top">

last\_login\_time

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

The local time that the user last logged in.

</td>
</tr>
<tr>
<td valign="top">

user\_type

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

A value that indicates whether the user is a regular user, or a role, or a user extended as a role. And whether the user, role, or extended role can be altered \(mutable\) or removed. Possible values:


<dl>
<dt><b>

1

</b></dt>
<dd>

Immutable system role.



</dd><dt><b>

5

</b></dt>
<dd>

Mutable system role



</dd><dt><b>

9

</b></dt>
<dd>

Immutable and removable system role.



</dd><dt><b>

12

</b></dt>
<dd>

Mutable and removable user.



</dd><dt><b>

13

</b></dt>
<dd>

Mutable and removable role.



</dd><dt><b>

14

</b></dt>
<dd>

Mutable and removable user extended as role.



</dd>
</dl>



</td>
</tr>
<tr>
<td valign="top">

user\_dn

</td>
<td valign="top">

CHAR \(1024\)

</td>
<td valign="top">

An LDAP Distinguished Name \(DN\) identifier for the user that is unique within a domain and across domains. The DN is used to authenticate with an LDAP server.

</td>
</tr>
<tr>
<td valign="top">

user\_dn\_cached\_at

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

The time that the user\_dn column was last cached. This value is used to determine whether to purge an old DN. Regardless of the database server local time zone, the value is stored in Coordinated Universal Time \(UTC\).

</td>
</tr>
<tr>
<td valign="top">

password\_creation\_time\_utc

</td>
<td valign="top">

TIMESTAMP WITH TIME ZONE

</td>
<td valign="top">

The UTC time that the password was created for the user.

</td>
</tr>
<tr>
<td valign="top">

last\_login\_time\_utc

</td>
<td valign="top">

TIMESTAMP WITH TIME ZONE

</td>
<td valign="top">

The UTC time that the user last logged in.

</td>
</tr>
<tr>
<td valign="top">

dual\_password

</td>
<td valign="top">

CHAR\(3\)

</td>
<td valign="top">

Whether the second part of a dual password is stored for the user. Three asterisks \(\*\*\*\) indicate that a second part is stored. NULL indicates that there’s no second part. You can return actual password hash values by querying the SYS.SYSUSERPASSWORD system view.

</td>
</tr>
<tr>
<td valign="top">

lock\_time

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Timestamp at which user was locked due to failed login attempts.

</td>
</tr>
</table>



<a name="loio191fd8e1a9594171a03df906f59e0a4f__section_gj1_wy1_4yb"/>

## Privileges

To use SAP HANA database REMOTE\_EXECUTE\_QUERY requires the REMOTE EXECUTE privilege on the remote source <hana\_relational\_container\_schema\>\_SOURCE.

-   See [REMOTE\_EXECUTE\_QUERY Usage Examples for Viewing System Views](https://help.sap.com/docs/SAP_HANA_DATA_LAKE/a898e08b84f21015969fa437e89860c8/ada51c0074354a5f99b60c14cffb653c.html).

**Related Information**  


[SYSUSER System View for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/3beae8f36c5f1014934e95d440287134.html "Each row in the SYS.SYSUSER system view describes a user, role, or schema in the system.") :arrow_upper_right:

