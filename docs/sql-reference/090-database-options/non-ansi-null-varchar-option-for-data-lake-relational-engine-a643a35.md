<!-- loioa643a35a84f21015bfbe86fabef32d77 -->

# NON\_ANSI\_NULL\_VARCHAR Option for Data Lake Relational Engine

Controls whether zero-length VARCHAR data is treated as NULLs for insert, load, and update operations.



<a name="loioa643a35a84f21015bfbe86fabef32d77__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa643a35a84f21015bfbe86fabef32d77__section_wfq_cxs_lrb"/>

## Syntax

```
NON_ANSI_NULL_VARCHAR = { ON | OFF };
```



<a name="loioa643a35a84f21015bfbe86fabef32d77__iq_refso_798"/>

## Allowed Values

ON, OFF



<a name="loioa643a35a84f21015bfbe86fabef32d77__iq_refso_799"/>

## Default

OFF



<a name="loioa643a35a84f21015bfbe86fabef32d77__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa643a35a84f21015bfbe86fabef32d77__iq_refso_800"/>

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



<a name="loioa643a35a84f21015bfbe86fabef32d77__iq_refso_801"/>

## Remarks

NON\_ANSI\_NULL\_VARCHAR lets you revert to non-ANSI behavior for treating zero-length VARCHAR data during load or update operations. When this option is set to OFF, zero-length VARCHAR data is stored as zero-length during load, insert, or update. When this option is set to ON, zero-length VARCHAR data is stored as NULLs on load, insert, or update.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

