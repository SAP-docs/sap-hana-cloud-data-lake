<!-- loioa63f778f84f21015a949fadfab293391 -->

# MAX\_QUERY\_TIME Option for Data Lake Relational Engine

Sets a time limit so that the optimizer can disallow very long queries.



<a name="loioa63f778f84f21015a949fadfab293391__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa63f778f84f21015a949fadfab293391__section_zx3_g24_hrb"/>

## Syntax

```
MAX_QUERY_TIME = <value>;
```



<a name="loioa63f778f84f21015a949fadfab293391__iq_refso_754"/>

## Allowed Values

0 to 2<sup>32</sup> – 1 \(minutes\)



<a name="loioa63f778f84f21015a949fadfab293391__iq_refso_755"/>

## Default

0 \(disabled\)



<a name="loioa63f778f84f21015a949fadfab293391__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa63f778f84f21015a949fadfab293391__iq_refso_756"/>

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



<a name="loioa63f778f84f21015a949fadfab293391__iq_refso_757"/>

## Remarks

If the query runs longer than the MAX\_QUERY\_TIME setting, data lake Relational Engine stops the query and sends a message to the user and the IQ message file. For example:

```
The operation has been canceled -- Max_Query_Time exceeded.
```

MAX\_QUERY\_TIME applies only to queries and not to any SQL statement that is modifying the contents of the database.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

