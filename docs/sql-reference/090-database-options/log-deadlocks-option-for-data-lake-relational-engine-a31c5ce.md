<!-- loioa31c5ce584f21015bb89fdbcca8c9910 -->

# LOG\_DEADLOCKS Option for Data Lake Relational Engine

Controls whether deadlock reporting is turned on or off.



<a name="loioa31c5ce584f21015bb89fdbcca8c9910__section_d5v_fkr_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa31c5ce584f21015bb89fdbcca8c9910__section_z42_4vs_lrb"/>

## Syntax

```
LOG_DEADLOCKS = { ON | OFF }
```



## Allowed values

ON, OFF



## Default

OFF



<a name="loioa31c5ce584f21015bb89fdbcca8c9910__section_eym_3fc_3qb"/>

## Privileges

Privilege Category: SYSTEM

Requires the SET ANY CUSTOMER SYSTEM OPTION system privilege to set this database option.



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

No

</td>
<td valign="top">

No

</td>
</tr>
</table>



## Remarks

When this option is set to On, the database server logs information about deadlocks in an internal buffer. The size of the buffer is fixed at 10000 bytes. The contents of the buffer are retained when this option is set to Off.

When deadlock occurs, information is reported for only those connections involved in the deadlock. The order in which connections are reported is based on which connection is waiting for which row. For thread deadlocks, information is reported about all connections.

When you have deadlock reporting turned on, you can also use the Deadlock system event to take action when a deadlock occurs.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

