<!-- loioa87ed92684f210159019e8efd0f5335c -->

# CREATE\_HG\_AND\_FORCE\_PHYSICAL\_DELETE Option for Data Lake Relational Engine

Governs 16.1 tiered HG index delete behavior.



<a name="loioa87ed92684f210159019e8efd0f5335c__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa87ed92684f210159019e8efd0f5335c__section_hgr_vb4_hrb"/>

## Syntax

```
CREATE_HG_AND_FORCE_PHYSICAL_DELETE = { ON | OFF };
```



## Allowed Values

ON, OFF



## Default

ON



<a name="loioa87ed92684f210159019e8efd0f5335c__section_k3c_gxb_3qb"/>

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

CREATE\_HG\_AND\_FORCE\_PHYSICAL\_DELETE determines whether delete operation physically removes rows from an HG immediately or defers the removal to a point later in the load:

-   Setting CREATE\_HG\_AND\_FORCE\_PHYSICAL\_DELETE to ON \(default\) instructs data lake Relational Engine to perform a physical delete, which increases the performance of some queries \(link in .. list and ordered projection, for example\), but can cause delete queries on tables with tiered HG indexes to run more slowly.

-   Setting CREATE\_HG\_AND\_FORCE\_PHYSICAL\_DELETE to OFF instructs data lake Relational Engine to perform a virtual or deferred delete, which improves delete query performance, but can impact queries on tables with tiered HG indexes.


Set CREATE\_HG\_AND\_FORCE\_PHYSICAL\_DELETE before creating a tiered HG column index. It does not affect preexisting HG indexes. It has no effect on sp\_iqrebuildindex. This option persists through the life of the tiered HG index, and cannot be changed or modified unless the index is dropped and the option toggled before re-creating the index \(sp\_iqrebuildindex cannot modify the status of the index\).

> ### Note:  
> sp\_iqrebuildindex output includes a Force Physical Delete column that identifies the status of this option.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

