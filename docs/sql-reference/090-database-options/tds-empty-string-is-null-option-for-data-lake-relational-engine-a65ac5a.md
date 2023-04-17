<!-- loioa65ac5a084f2101595eb973cc2b9a99f -->

# TDS\_EMPTY\_STRING\_IS\_NULL Option for Data Lake Relational Engine

Controls whether empty strings are returned as NULL or a string containing one blank character for TDS connections.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa65ac5a084f2101595eb973cc2b9a99f__section_e3s_2d1_mrb"/>

## Syntax

```
TDS_EMPTY_STRING_IS_NULL = { ON | OFF }
```



<a name="loioa65ac5a084f2101595eb973cc2b9a99f__iq_refso_980"/>

## Allowed Values

ON, OFF



<a name="loioa65ac5a084f2101595eb973cc2b9a99f__iq_refso_981"/>

## Default

OFF



<a name="loioa65ac5a084f2101595eb973cc2b9a99f__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa65ac5a084f2101595eb973cc2b9a99f__iq_refso_325"/>

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



<a name="loioa65ac5a084f2101595eb973cc2b9a99f__iq_refso_982"/>

## Remarks

TDS\_EMPTY\_STRING\_IS\_NULL is set to OFF by default and empty strings are returned as a string containing one blank character for TDS connections. When this option is set to ON, empty strings are returned as NULL strings for TDS connections. Non-TDS connections distinguish empty strings from NULL strings.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

