<!-- loioa62c8c6584f210159b5f93f8f482b38f -->

# ANSI\_PERMISSIONS Option \[TSQL\] for Data Lake Relational Engine

Controls permissions checking for DELETE and UPDATE statements.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa62c8c6584f210159b5f93f8f482b38f__section_u1n_l5b_qkb"/>

## Syntax

```
ANSI_PERMISSIONS = { ON | OFF }
```



<a name="loioa62c8c6584f210159b5f93f8f482b38f__iq_refso_333"/>

## Allowed Values

ON, OFF



<a name="loioa62c8c6584f210159b5f93f8f482b38f__iq_refso_334"/>

## Default

ON



<a name="loioa62c8c6584f210159b5f93f8f482b38f__section_eym_3fc_3qb"/>

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

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
</table>



<a name="loioa62c8c6584f210159b5f93f8f482b38f__iq_refso_335"/>

## Remarks

With ANSI\_PERMISSIONS ON, SQL92 permission requirements for DELETE and UPDATE statements are checked. The default value is OFF in SAP Adaptive Server Enterprise. This table outlines the differences:


<table>
<tr>
<th valign="top">

SQL Statement



</th>
<th valign="top">

Permissions Required with ANSI\_PERMISSIONS OFF



</th>
<th valign="top">

Permissions Required with ANSI\_PERMISSIONS ON



</th>
</tr>
<tr>
<td valign="top">

UPDATE



</td>
<td valign="top">

UPDATE permission on the columns where values are being set



</td>
<td valign="top">

-   UPDATE permission on the columns where values are being set

-   SELECT permission on all columns appearing in the WHERE clause.

-   SELECT permission on all columns on the right side of the SET clause.




</td>
</tr>
<tr>
<td valign="top">

DELETE



</td>
<td valign="top">

DELETE permission on table



</td>
<td valign="top">

-   DELETE permission on table.

-   SELECT permission on all columns appearing in the WHERE clause.




</td>
</tr>
</table>

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

