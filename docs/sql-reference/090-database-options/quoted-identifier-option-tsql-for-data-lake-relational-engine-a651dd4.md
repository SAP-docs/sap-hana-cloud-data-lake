<!-- loioa651dd4f84f21015b4c7b6295b1306f8 -->

# QUOTED\_IDENTIFIER Option \[TSQL\] for Data Lake Relational Engine

Controls the interpretation of strings that are enclosed in double quotes.



<a name="loioa651dd4f84f21015b4c7b6295b1306f8__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa651dd4f84f21015b4c7b6295b1306f8__section_ybv_2gy_lrb"/>

## Syntax

```
QUOTED_IDENTIFIER = { ON | OFF }
```



<a name="loioa651dd4f84f21015b4c7b6295b1306f8__iq_refso_913"/>

## Allowed Values

ON, OFF



<a name="loioa651dd4f84f21015b4c7b6295b1306f8__iq_refso_914"/>

## Default

-   ON
-   OFF – for Open Client connections.



<a name="loioa651dd4f84f21015b4c7b6295b1306f8__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa651dd4f84f21015b4c7b6295b1306f8__iq_refso_325"/>

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



<a name="loioa651dd4f84f21015b4c7b6295b1306f8__iq_refso_915"/>

## Remarks

QUOTED\_IDENTIFIER controls whether strings enclosed in double quotes are interpreted as identifiers \(ON\) or as literal strings \(OFF\). This option is included for Transact-SQL compatibility.

Interactive SQL sets QUOTED\_IDENTIFIER temporarily to ON, if it is set to OFF. A message is displayed informing you of this change. The change is in effect only for the Interactive SQL connection. The JDBC driver also temporarily sets QUOTED\_IDENTIFIER to ON.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

