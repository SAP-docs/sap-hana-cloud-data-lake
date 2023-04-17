<!-- loio814661016ce2101499ddd334930bf1ed -->

# MIN\_PASSWORD\_LENGTH Option for Data Lake Relational Engine

Sets the minimum length for new passwords in the database.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio814661016ce2101499ddd334930bf1ed__section_zx3_g24_hrb"/>

## Syntax

```
MIN_PASSWORD_LENGTH = <value>
```



## Allowed Values

Integer

The value is in bytes. For single-byte character sets, this value is the same as the number of characters.



## Default

6



<a name="loio814661016ce2101499ddd334930bf1ed__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: SECURITY

Requires the SET ANY CUSTOMER SECURITY OPTION system privilege to set this database option.



<a name="loio814661016ce2101499ddd334930bf1ed__min-password-length-option-scope"/>

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

This option allows the database administrator to impose a minimum length on all new passwords for greater security. Existing passwords are not affected. Passwords have a maximum length of 255 bytes and are case sensitive.



Set the minimum length for new passwords to 6 bytes.

```
SET OPTION PUBLIC.min_password_length = 6;
```

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

