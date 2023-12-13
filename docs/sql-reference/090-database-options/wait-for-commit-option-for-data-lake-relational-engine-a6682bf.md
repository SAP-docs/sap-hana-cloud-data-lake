<!-- loioa6682bf784f2101592f6d6affcce9cc7 -->

# WAIT\_FOR\_COMMIT Option for Data Lake Relational Engine

Determines when foreign key integrity is checked as data is manipulated.



<a name="loioa6682bf784f2101592f6d6affcce9cc7__section_x2s_htr_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa6682bf784f2101592f6d6affcce9cc7__section_el3_hrh_mrb"/>

## Syntax

```
WAIT_FOR_COMMIT = { ON | OFF };
```



<a name="loioa6682bf784f2101592f6d6affcce9cc7__iq_refso_1085"/>

## Allowed Values

ON, OFF



<a name="loioa6682bf784f2101592f6d6affcce9cc7__iq_refso_1086"/>

## Default

OFF



<a name="loioa6682bf784f2101592f6d6affcce9cc7__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa6682bf784f2101592f6d6affcce9cc7__iq_refso_1087"/>

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



<a name="loioa6682bf784f2101592f6d6affcce9cc7__iq_refso_1088"/>

## Remarks

If this option is set to ON, the database does not check foreign key integrity until the next COMMIT statement. Otherwise, all foreign keys not created with the CHECK ON COMMIT option are checked as they are inserted, updated, or deleted.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

