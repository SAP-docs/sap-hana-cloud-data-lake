<!-- loioa63ac6b684f210159d6aeaadb339e955 -->

# ISOLATION\_LEVEL Option for Data Lake Relational Engine

Controls the locking isolation level for catalog store tables.



<a name="loioa63ac6b684f210159d6aeaadb339e955__section_qc4_fkr_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa63ac6b684f210159d6aeaadb339e955__section_zx3_g24_hrb"/>

## Syntax

```
ISOLATION_LEVEL = <value>;
```



<a name="loioa63ac6b684f210159d6aeaadb339e955__iq_refso_645"/>

## Allowed Values

-   0 – Allow dirty reads, nonrepeatable reads, and phantom rows.
-   1 – Prevent dirty reads. Allow nonrepeatable reads and phantom rows.
-   2 – Prevent dirty reads and guarantee repeatable reads. Allow phantom rows.
-   3 – Serializable. Do not allow dirty reads, guarantee repeatable reads, and do not allow phantom rows.



<a name="loioa63ac6b684f210159d6aeaadb339e955__iq_refso_646"/>

## Default

-   0

-   1 for Open Client and JDBC connections




<a name="loioa63ac6b684f210159d6aeaadb339e955__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa63ac6b684f210159d6aeaadb339e955__iq_refso_325"/>

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



<a name="loioa63ac6b684f210159d6aeaadb339e955__iq_refso_647"/>

## Remarks

ISOLATION\_LEVEL determines the isolation level for tables in the catalog store. Data lake Relational Engine always enforces level 3 for tables in the IQ store. Level 3 is equivalent to ANSI level 4.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

