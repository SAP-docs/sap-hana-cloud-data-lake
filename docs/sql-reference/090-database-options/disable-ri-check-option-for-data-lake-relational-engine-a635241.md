<!-- loioa635241084f21015aab4acfa1a173538 -->

# DISABLE\_RI\_CHECK Option for Data Lake Relational Engine

Allows load, insert, update, or delete operations to bypass the referential integrity check, improving performance.



<a name="loioa635241084f21015aab4acfa1a173538__section_ajq_xqq_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa635241084f21015aab4acfa1a173538__disable_re_check_syntax1"/>

## Syntax

```
DISABLE_RI_CHECK = { ON | OFF };
```



<a name="loioa635241084f21015aab4acfa1a173538__disable_ri_check_values1"/>

## Allowed Values

ON, OFF



<a name="loioa635241084f21015aab4acfa1a173538__disable_ri_check_default1"/>

## Default

OFF



<a name="loioa635241084f21015aab4acfa1a173538__disable_ri_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa635241084f21015aab4acfa1a173538__disable_ri_check_scope1"/>

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



<a name="loioa635241084f21015aab4acfa1a173538__disable_ri_check_remarks1"/>

## Remarks

Users are responsible for ensuring that no referential integrity violation occurs during requests while DISABLE\_RI\_CHECK is set to ON.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[DISABLE_RI_CHECK Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/4b9fb5d8d0e24b1984950aa752543793.html "Allows load, insert, update, or delete operations to bypass the referential integrity check, improving performance.") :arrow_upper_right:

