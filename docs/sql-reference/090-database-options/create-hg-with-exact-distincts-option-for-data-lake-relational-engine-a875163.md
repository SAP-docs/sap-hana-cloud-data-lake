<!-- loioa875163484f210159baec0b8087c7188 -->

# CREATE\_HG\_WITH\_EXACT\_DISTINCTS Option for Data Lake Relational Engine

Determines whether the database engine creates tiered HG or single-tiered HG indexes.



<a name="loioa875163484f210159baec0b8087c7188__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa875163484f210159baec0b8087c7188__blocking_section1"/>

## Syntax

```
CREATE_HG_WITH_EXACT_DISTINCTS = { ON | OFF };
```



## Allowed Values

ON, OFF



## Default

OFF



<a name="loioa875163484f210159baec0b8087c7188__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



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



## Remarks

CREATE\_HG\_WITH\_EXACT\_DISTINCTS determines whether the database engine creates HG indexes as single HG or tiered HG:

-   If CREATE\_HG\_WITH\_EXACT\_DISTINCTS='ON' – all subsequent HG indexes explicitly created with a CREATE INDEX command or implicitly creating or altering a table with a PRIMARY KEY or a FOREIGN KEY declaration, will be non-tiered HG indexes.
-   If CREATE\_HG\_WITH\_EXACT\_DISTINCTS='OFF' – all subsequent HG indexes explicitly created with a CREATE INDEX command or implicitly creating or altering a table with a PRIMARY KEY or a FOREIGN KEY declaration, will be tiered HG.

This option is ON by default in all newly created 16.1 databases. To take advantage of the tiered structure, set this option to OFF. Use sp\_iqrebuildindex to convert non-tiered HG indexes to tiered HG and vice versa.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

