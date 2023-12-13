<!-- loioa62f280e84f21015a126e6158ee806f0 -->

# CHAINED Option \[TSQL\] for Data Lake Relational Engine

Controls transaction mode in the absence of a BEGIN TRANSACTION statement.



<a name="loioa62f280e84f21015a126e6158ee806f0__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa62f280e84f21015a126e6158ee806f0__section_xdr_2ry_brb"/>

## Syntax

```
CHAINED = { ON | OFF };
```



<a name="loioa62f280e84f21015a126e6158ee806f0__iq_refso_394"/>

## Allowed Values

ON, OFF



<a name="loioa62f280e84f21015a126e6158ee806f0__iq_refso_395"/>

## Default

-   ON

-   OFF for Open Client and JDBC connections




<a name="loioa62f280e84f21015a126e6158ee806f0__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa62f280e84f21015a126e6158ee806f0__iq_refso_325"/>

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



<a name="loioa62f280e84f21015a126e6158ee806f0__iq_refso_396"/>

## Remarks

Controls the Transact-SQL transaction mode. In unchained mode \(CHAINED = OFF\) each statement is committed individually unless an explicit BEGIN TRANSACTION statement is executed to start a transaction. In chained mode \(CHAINED = ON\) a transaction is implicitly started before any data retrieval or modification statement. For SAP Adaptive Server Enterprise, the default setting is OFF.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

