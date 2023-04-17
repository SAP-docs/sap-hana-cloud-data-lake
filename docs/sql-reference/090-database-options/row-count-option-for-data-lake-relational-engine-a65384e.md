<!-- loioa65384ed84f21015957cddd34cdac464 -->

# ROW\_COUNT Option for Data Lake Relational Engine

Limits the number of rows returned from a query.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa65384ed84f21015957cddd34cdac464__section_zx3_g24_hrb"/>

## Syntax

```
ROW_COUNT = <value>
```



<a name="loioa65384ed84f21015957cddd34cdac464__iq_refso_924"/>

## Allowed Values

Integer



<a name="loioa65384ed84f21015957cddd34cdac464__iq_refso_925"/>

## Default

0 \(no limit on rows returned\)



<a name="loioa65384ed84f21015957cddd34cdac464__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa65384ed84f21015957cddd34cdac464__iq_refso_926"/>

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



<a name="loioa65384ed84f21015957cddd34cdac464__iq_refso_927"/>

## Remarks

When this runtime option is set to a nonzero value, query processing stops after the specified number of rows.

This option affects only statements with the keyword SELECT and does not affect UPDATE and DELETE statements.

The SELECT statement keywords FIRST and TOP also limit the number of rows returned from a query. Using FIRST is the same as setting the ROW\_COUNT database option to 1. Using TOP is the same as setting ROW\_COUNT to the same number of rows. If both TOP and ROW\_COUNT are set, then the value of TOP takes precedence.

The ROW\_COUNT option could produce non-deterministic results when used in a query involving global variables, system functions or proxy tables. Such queries are partly executed using CIS \(Component Integrated Services\). In such cases, use SELECT TOP *<n\>* instead of setting ROW\_COUNT, or set the global variable to a local one and use that local variable in the query.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[QUERY\_ROWS\_RETURNED\_LIMIT Option for Data Lake Relational Engine](query-rows-returned-limit-option-for-data-lake-relational-engine-a650455.md "Sets the row threshold for rejecting queries based on estimated size of result set.")

[SELECT Statement for Data Lake Relational Engine](../080-sql-statements/select-statement-for-data-lake-relational-engine-a624e72.md "Retrieves information from the database.")

