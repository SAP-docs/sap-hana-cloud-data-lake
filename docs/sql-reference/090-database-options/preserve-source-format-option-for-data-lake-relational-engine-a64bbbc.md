<!-- loioa64bbbc584f210159564c4331b227c52 -->

# PRESERVE\_SOURCE\_FORMAT Option for Data Lake Relational Engine

Controls whether the original source definition of procedures, views, and event handlers is saved in system files. If saved, the formatted source is saved in the column source in SYSTABLE, SYSPROCEDURE, and SYSEVENT.



<a name="loioa64bbbc584f210159564c4331b227c52__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa64bbbc584f210159564c4331b227c52__section_yqz_4ys_lrb"/>

## Syntax

```
PRESERVE_SOURCE_FORMAT = { ON | OFF };
```



<a name="loioa64bbbc584f210159564c4331b227c52__iq_refso_862"/>

## Allowed Values

ON, OFF



<a name="loioa64bbbc584f210159564c4331b227c52__iq_refso_863"/>

## Default

ON



<a name="loioa64bbbc584f210159564c4331b227c52__section_eym_3fc_3qb"/>

## Privileges

Privilege Category: SYSTEM

Requires the SET ANY CUSTOMER SYSTEM OPTION system privilege to set this database option.



<a name="loioa64bbbc584f210159564c4331b227c52__iq_refso_864"/>

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



<a name="loioa64bbbc584f210159564c4331b227c52__iq_refso_865"/>

## Remarks

When PRESERVE\_SOURCE\_FORMAT is ON, the server saves the formatted source from CREATE and ALTER statements on procedures, views, and events, and puts original source definition in the source column of the appropriate system table.

Unformatted source text is stored in the same system tables, in the columns proc\_defn, and view\_defn. The formatted source column allows you to view the definitions with the spacing, comments, and case that you want.

This option can be turned off to reduce space used to save object definitions in the database. The option can be set only for the PUBLIC role.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

