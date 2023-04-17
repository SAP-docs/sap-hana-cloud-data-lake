<!-- loioa44b400584f2101595c8d290ef6c3ef5 -->

# MIN\_ROLE\_ADMINS Option for Data Lake Relational Engine

Configures of the minimum number of required administrators for all roles.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa44b400584f2101595c8d290ef6c3ef5__section_zx3_g24_hrb"/>

## Syntax

```
MIN_ROLE_ADMINS = <value>
```



<a name="loioa44b400584f2101595c8d290ef6c3ef5__iq_refso_698"/>

## Allowed Values

1 to 10



<a name="loioa44b400584f2101595c8d290ef6c3ef5__iq_refso_699"/>

## Default

1



<a name="loioa44b400584f2101595c8d290ef6c3ef5__section_eym_3fc_3qb"/>

## Privileges

Privilege Category: SECURITY

Requires the SET ANY CUSTOMER SECURITY OPTION system privilege to set this database option.



<a name="loioa44b400584f2101595c8d290ef6c3ef5__iq_refso_700"/>

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



<a name="loioa44b400584f2101595c8d290ef6c3ef5__iq_refso_701"/>

## Remarks

This option sets the minimum number of required administrators for all roles. This value applies to the minimum number of role administrators for each role, not the minimum number or role administrators for the total number of roles. When dropping roles or users, this value ensures that you never create a scenario where there are no users and roles left with sufficient system privilege to manage the remaining users and roles.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

