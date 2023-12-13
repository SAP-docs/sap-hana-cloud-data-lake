<!-- loioa638e37684f210159ab5d9e9a28e3435 -->

# IDENTITY\_ENFORCE\_UNIQUENESS Option for Data Lake Relational Engine

Creates a unique HG index on each IDENTITY/AUTOINCREMENT column, if the column is not already a primary key.



<a name="loioa638e37684f210159ab5d9e9a28e3435__section_vzr_mjr_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa638e37684f210159ab5d9e9a28e3435__section_ndh_qks_lrb"/>

## Syntax

```
IDENTITY_ENFORCE_UNIQUENESS = { ON | OFF };
```



<a name="loioa638e37684f210159ab5d9e9a28e3435__iq_refso_601"/>

## Allowed Values

ON, OFF



<a name="loioa638e37684f210159ab5d9e9a28e3435__iq_refso_602"/>

## Default

OFF



<a name="loioa638e37684f210159ab5d9e9a28e3435__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa638e37684f210159ab5d9e9a28e3435__iq_refso_603"/>

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



<a name="loioa638e37684f210159ab5d9e9a28e3435__iq_refso_604"/>

## Remarks

When option is set ON, HG indexes are created on future identity columns. The index can only be deleted if the deleting user is the only one using the table and the table is not a local temporary table.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[QUERY\_PLAN Option for Data Lake Relational Engine](query-plan-option-for-data-lake-relational-engine-a64d3bd.md "Specifies whether or not additional query plans are printed to the data lake Relational Engine message file.")

