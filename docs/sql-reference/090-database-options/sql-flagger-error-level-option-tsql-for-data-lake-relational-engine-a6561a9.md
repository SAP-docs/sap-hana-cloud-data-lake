<!-- loioa6561a9684f21015b8c7dfeda2c69941 -->

# SQL\_FLAGGER\_ERROR\_LEVEL Option \[TSQL\] for Data Lake Relational Engine

Controls the behavior in response to any SQL code that is not part of the specified standard.



<a name="loioa6561a9684f21015b8c7dfeda2c69941__section_fq2_gpq_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa6561a9684f21015b8c7dfeda2c69941__sql_flagger_error_syntax1"/>

## Syntax

```
SQL_FLAGGER_ERROR_LEVEL = <string_expression>
```



<a name="loioa6561a9684f21015b8c7dfeda2c69941__sql_flagger_error_values1"/>

## Allowed Values

-   OFF
-   SQL:1992/EntrySQL:1992/Intermediate
-   SQL:1992/Full
-   SQL:1999/Core
-   SQL:1999/Package
-   SQL:2003/Core
-   SQL:2003/Package



<a name="loioa6561a9684f21015b8c7dfeda2c69941__sql_flagger_error_default1"/>

## Default

OFF



<a name="loioa6561a9684f21015b8c7dfeda2c69941__sql_flagger_error_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa6561a9684f21015b8c7dfeda2c69941__sql_flagger_error_scope1"/>

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



<a name="loioa6561a9684f21015b8c7dfeda2c69941__sql_flagger_error_remarks1"/>

## Remarks

Flags as an error any SQL code that is not part of a specified standard. For example, specifying SQL:2003/Package causes the database server to flag syntax that is not full SQL/2003 syntax.

For compatibility with previous data lake Relational Engine versions, the following values are also accepted, and are mapped as specified. Compatibility values for SQL\_FLAGGER\_ERROR\_LEVEL are:

-   E – flag syntax that is not entry-level SQL92 syntax. Corresponds to SQL:1992/Entry.
-   I – flag syntax that is not intermediate-level SQL92 syntax. Corresponds to SQL:1992/Intermediate.
-   F – flag syntax that is not full-SQL92 syntax. Corresponds to SQL:1992/Full.
-   W – allow all supported syntax. Corresponds to OFF.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[SQL_FLAGGER_ERROR_LEVEL Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/8d0419f947274ddfb7c2be8bb35ac237.html "Controls the behavior in response to any SQL code that is not part of the specified standard.") :arrow_upper_right:

