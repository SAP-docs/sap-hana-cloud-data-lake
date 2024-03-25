<!-- loioa31619c984f2101582cbbe66dee24be8 -->

# BLOCKING\_TIMEOUT Option for Data Lake Relational Engine

Controls the length of time a transaction waits to obtain a lock. BLOCKING\_TIMEOUT is only supported when connectd directly to the co-ordinator.



<a name="loioa31619c984f2101582cbbe66dee24be8__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa31619c984f2101582cbbe66dee24be8__blocking_timeout_refsyn1"/>

## Syntax

```
BLOCKING_TIMEOUT = <number_expression>
```



<a name="loioa31619c984f2101582cbbe66dee24be8__blocking_timeout_values1"/>

## Allowed Values

Integer, in milliseconds.



<a name="loioa31619c984f2101582cbbe66dee24be8__blocking_timeout_default1"/>

## Default

0



<a name="loioa31619c984f2101582cbbe66dee24be8__blocking_timeout_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa31619c984f2101582cbbe66dee24be8__blocking_timeout_scope1"/>

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



<a name="loioa31619c984f2101582cbbe66dee24be8__blocking_timeout_remarks1"/>

## Remarks

When the blocking option is on, any transaction attempting to obtain a lock that conflicts with an existing lock waits for the indicated number of milliseconds for the conflicting lock to be released. If the lock is not released within blocking\_timeout milliseconds, an error is returned for the waiting transaction.

Set the option to 0 to force all transactions attempting to obtain a lock to wait until all conflicting transactions release their locks.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[BLOCKING_TIMEOUT Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/8104fc0cdf4143caa395e241e58db92a.html "Controls the length of time a transaction waits to obtain a lock. BLOCKING_TIMEOUT is only supported when connectd directly to the co-ordinator.") :arrow_upper_right:

