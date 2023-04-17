<!-- loioa62e391684f21015b33ae00f1e29d81a -->

# BLOCKING Option for Data Lake Relational Engine

Controls the behavior in response to locking conflicts.BLOCKING isn't supported on worker nodes.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa62e391684f21015b33ae00f1e29d81a__blocking_section1"/>

## Syntax

```
BLOCKING = { ON | OFF }
```



<a name="loioa62e391684f21015b33ae00f1e29d81a__section_mzg_b4y_brb"/>

## Allowed Values

ON, OFF



<a name="loioa62e391684f21015b33ae00f1e29d81a__blocking_default1"/>

## Default

OFF



<a name="loioa62e391684f21015b33ae00f1e29d81a__blocking_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa62e391684f21015b33ae00f1e29d81a__blocking_scope1"/>

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



<a name="loioa62e391684f21015b33ae00f1e29d81a__blocking_remarks1"/>

## Remarks

When BLOCKING is off, a transaction receives an error when it attempts a write operation and is blocked by the read lock of another transaction.

When BLOCKING is on, any transaction attempting to obtain a lock that conflicts with an existing lock held by another transaction waits until every conflicting lock is released or until the BLOCKING\_TIMEOUT is reached. If the lock isn’t released within BLOCKING\_TIMEOUT milliseconds, then an error is returned for the waiting transaction.

> ### Note:  
> BLOCKING isn't supported on worker nodes of the multiplex cluster. SAP HANA servers can only access worker nodes.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[BLOCKING Option for Data Lake Relational Engine](blocking-option-for-data-lake-relational-engine-a62e391.md "Controls the behavior in response to locking conflicts. BLOCKING isn't supported on worker nodes.")

[BLOCKING\_TIMEOUT Option for Data Lake Relational Engine](blocking-timeout-option-for-data-lake-relational-engine-a31619c.md "Controls the length of time a transaction waits to obtain a lock. BLOCKING_TIMEOUT is only supported when connectd directly to the co-ordinator.")

[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[BLOCKING Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/c5646d5b730a431dacb60c07624d25db.html "Controls the behavior in response to locking conflicts. BLOCKING isn&apos;t supported on worker nodes.") :arrow_upper_right:

