<!-- loioa601530984f21015b564e47a01f5fe91 -->

# ENABLE\_LOB\_VARIABLES Option for Data Lake Relational Engine

Controls the data type conversion of large object variables.



<a name="loioa601530984f21015b564e47a01f5fe91__section_ipl_jgr_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa601530984f21015b564e47a01f5fe91__section_sky_yzh_3rb"/>

## Syntax

```
ENABLE_LOB_VARIABLES = { ON | OFF };
```



<a name="loioa601530984f21015b564e47a01f5fe91__iq_iquda_141"/>

## Allowed Values

ON, OFF



<a name="loioa601530984f21015b564e47a01f5fe91__iq_iquda_142"/>

## Default

OFF



<a name="loioa601530984f21015b564e47a01f5fe91__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa601530984f21015b564e47a01f5fe91__iq_iquda_143"/>

## Scope


<table>
<tr>
<th valign="top">

 

</th>
<th valign="top">

PUBLIC Role

</th>
<th valign="top">

For Current User

</th>
<th valign="top">

For Other Users

</th>
</tr>
<tr>
<td valign="top">

Allowed to set permanently?

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

Allowed to set temporarily?

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes \(current connection only\)

</td>
<td valign="top">

No

</td>
</tr>
</table>



<a name="loioa601530984f21015b564e47a01f5fe91__iq_iquda_144"/>

## Remarks

ENABLE\_LOB\_VARIABLES controls the data type conversion of large object variables.

A LONG VARCHAR variable is implicitly converted to a VARCHAR data type and truncated at 32 KB. A LONG BINARY variable is implicitly converted to a VARBINARY data type and truncated at 32 KB. When ENABLE\_LOB\_VARIABLES is OFF and the length of LOB data is larger than 32 KB, an error is reported

When ENABLE\_LOB\_VARIABLES is ON, large object variables of any size retain their original data type and size.



<a name="loioa601530984f21015b564e47a01f5fe91__iq_iquda_145"/>

## Example

Retain the data type and size of large object variables greater than 32 KB:

```
SET TEMPORARY OPTION ENABLE_LOB_VARIABLES = ON;
```

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

