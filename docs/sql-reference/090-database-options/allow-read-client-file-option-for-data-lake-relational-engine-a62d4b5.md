<!-- loioa62d4b5484f21015a1f8f294d6dbfd6a -->

# ALLOW\_READ\_CLIENT\_FILE Option for Data Lake Relational Engine

Enables client-side data transfer.



<a name="loioa62d4b5484f21015a1f8f294d6dbfd6a__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa62d4b5484f21015a1f8f294d6dbfd6a__section_u1n_l5b_qkb"/>

## Syntax

```
ALLOW_READ_CLIENT_FILE = { ON | OFF };
```



## Allowed Values

ON, OFF



## Default

OFF



<a name="loioa62d4b5484f21015a1f8f294d6dbfd6a__section_eym_3fc_3qb"/>

## Privileges

Privilege Category: SECURITY

Requires the SET ANY CUSTOMER SECURITY OPTION system privilege to set this database option.



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



## Remarks

Enable this option to read from files on a client computer, for example by using the READ\_CLIENT\_FILE function.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

