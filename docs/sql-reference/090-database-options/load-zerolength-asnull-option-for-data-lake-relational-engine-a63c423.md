<!-- loioa63c423984f21015a9d6d9ab3c0675cb -->

# LOAD\_ZEROLENGTH\_ASNULL Option for Data Lake Relational Engine

Specifies LOAD statement behavior under certain conditions.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa63c423984f21015a9d6d9ab3c0675cb__section_nrd_dws_lrb"/>

## Syntax

```
LOAD_ZEROLENGTH_ASNULL = { ON | OFF }
```



<a name="loioa63c423984f21015a9d6d9ab3c0675cb__iq_refso_685"/>

## Allowed Values

ON, OFF



<a name="loioa63c423984f21015a9d6d9ab3c0675cb__iq_refso_686"/>

## Default

OFF



<a name="loioa63c423984f21015a9d6d9ab3c0675cb__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa63c423984f21015a9d6d9ab3c0675cb__iq_refso_685a"/>

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



<a name="loioa63c423984f21015a9d6d9ab3c0675cb__iq_refso_687"/>

## Remarks

This option specifies LOAD statement behavior under these conditions:

-   Inserting a zero-length data value into a column of data type CHAR, VARCHAR, LONG VARCHAR, BINARY, VARBINARY, or LONG BINARY, and
-   A NULL column-spec; for example, NULL\(ZEROS\) or NULL\(BLANKS\) is also given for that same column.

Set LOAD\_ZEROLENGTH\_ASNULL ON to load a zero-length value as NULL when the above conditions are met.

Set LOAD\_ZEROLENGTH\_ASNULL OFF to load a zero-length value as zero-length, subject to the setting of option NON\_ANSI\_NULL\_VARCHAR.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[NON\_ANSI\_NULL\_VARCHAR Option for Data Lake Relational Engine](non-ansi-null-varchar-option-for-data-lake-relational-engine-a643a35.md "Controls whether zero-length VARCHAR data is treated as NULLs for insert, load, and update operations.")

