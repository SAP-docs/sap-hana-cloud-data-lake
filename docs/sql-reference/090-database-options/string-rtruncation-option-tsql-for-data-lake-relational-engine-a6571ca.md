<!-- loioa6571caf84f210159246b755dd4c1d74 -->

# STRING\_RTRUNCATION Option \[TSQL\] for Data Lake Relational Engine

Determines whether an error is raised when an INSERT or UPDATE truncates a CHAR or VARCHAR string.



<a name="loioa6571caf84f210159246b755dd4c1d74__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa6571caf84f210159246b755dd4c1d74__section_zx3_g24_hrb"/>

## Syntax

```
STRING_RTRUNCATION = <value>;
```



<a name="loioa6571caf84f210159246b755dd4c1d74__iq_refso_953"/>

## Allowed Values

ON, OFF



<a name="loioa6571caf84f210159246b755dd4c1d74__iq_refso_954"/>

## Default

ON



<a name="loioa6571caf84f210159246b755dd4c1d74__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa6571caf84f210159246b755dd4c1d74__iq_refso_325"/>

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



<a name="loioa6571caf84f210159246b755dd4c1d74__iq_refso_955"/>

## Remarks

If the truncated characters consist only of spaces, no exception is raised. ON corresponds to SQL92 behavior. When STRING\_RTRUNCATION is OFF, the exception is not raised and the character string is silently truncated. If the option is ON and an error is raised, a ROLLBACK occurs.

This option was OFF by default prior to data lake Relational Engine. It can safely be set to OFF for backward compatibility. However, the ON setting is preferable to identify statements where truncation may cause data loss.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

