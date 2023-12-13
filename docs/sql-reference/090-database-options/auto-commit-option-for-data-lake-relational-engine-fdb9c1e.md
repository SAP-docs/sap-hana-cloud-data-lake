<!-- loiofdb9c1e166c841f2b0a20ade151a9051 -->

# AUTO\_COMMIT Option for Data Lake Relational Engine

Causes an automatic commit after every DML request.



<a name="loiofdb9c1e166c841f2b0a20ade151a9051__section_fc2_ncx_4zb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.
-   Connected directly to data lake Relational Engine **coordinator** as a data lake Relational Engine user.



<a name="loiofdb9c1e166c841f2b0a20ade151a9051__auto_commit_syntax1"/>

## Syntax

```
AUTO_COMMIT = { ON | OFF };
```



<a name="loiofdb9c1e166c841f2b0a20ade151a9051__auto_commit_values1"/>

## Allowed Values

ON, OFF



<a name="loiofdb9c1e166c841f2b0a20ade151a9051__auto_commit_default1"/>

## Default

OFF



<a name="loiofdb9c1e166c841f2b0a20ade151a9051__auto_commit_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loiofdb9c1e166c841f2b0a20ade151a9051__auto_commit_scope1"/>

## Scope


<table>
<tr>
<th valign="top">

 

</th>
<th valign="top">

PUBLIC role

</th>
<th valign="top">

For current user

</th>
<th valign="top">

For other users

</th>
</tr>
<tr>
<td valign="top">

Allowed to set permanently?

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

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



<a name="loiofdb9c1e166c841f2b0a20ade151a9051__auto_commit_remarks1"/>

## Remarks

If this option is set to On, then the database server automatically commits after every DML request. This option can only be set temporarily for a connection.

The AUTO\_COMMIT option cannot be set to ON if the AUTOCOMMIT\_DDL is currently set to OFF as these two options are contradictory.

> ### Note:  
> The AUTO\_COMMIT option is different from the chained option. Setting AUTO\_COMMIT to On forces the database server to commit after every request. Setting the CHAINED option to Off forces the database server to commit after each statement. This distinction is most important when executing a stored procedure. Setting the CHAINED option to Off results in a commit request after the execution of each individual statement within the procedure. Setting the AUTO\_COMMIT option to On results in a single commit request once the entire procedure finishes executing. In cases where automatic commit is necessary, it is much better to use the AUTO\_COMMIT option rather than the CHAINED option.

**Related Information**  


[AUTOCOMMIT\_DDL Option for Data Lake Relational Engine](autocommit-ddl-option-for-data-lake-relational-engine-a6a6389.md "Controls whether or not an automatic commit occurs after every DDL transaction.")

[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

