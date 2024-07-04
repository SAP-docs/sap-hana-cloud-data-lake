<!-- loio912d8f5b53a54ea5ad4c23fbf5198644 -->

# LOAD\_PREFETCH\_LOOKAHEAD Option for Data Lake Relational Engine

Specify a higher prefetch lookahead value or lets the system set automatically based on the IO latency to improve performance with the LOAD statement.



<a name="loio912d8f5b53a54ea5ad4c23fbf5198644__section_fq2_gpq_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio912d8f5b53a54ea5ad4c23fbf5198644__lookahead_syntax1"/>

## Syntax

```
LOAD_PREFETCH_LOOKAHEAD = <value>
```



<a name="loio912d8f5b53a54ea5ad4c23fbf5198644__lookahead_allowed_values1"/>

## Allowed Values


<table>
<tr>
<th valign="top">

Value

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

\-1

</td>
<td valign="top">

Disables adaptive prefetching. The original prefetch approach where the lookahead value is 1 is used.

</td>
</tr>
<tr>
<td valign="top">

0

</td>
<td valign="top">

Enables adaptive prefetching.

</td>
</tr>
<tr>
<td valign="top">

1 to 15

</td>
<td valign="top">

Specifies the lookahead value to use for adaptive prefetching to a maximum of 15.

</td>
</tr>
</table>



<a name="loio912d8f5b53a54ea5ad4c23fbf5198644__lookahead_default1"/>

## Default

0



<a name="loio912d8f5b53a54ea5ad4c23fbf5198644__load_prefetch_lookahead_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loio912d8f5b53a54ea5ad4c23fbf5198644__lookahead_scope1"/>

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

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[LOAD_PREFETCH_LOOKAHEAD Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/e245892799f64df68ade16f24f1ddfb0.html "Specify a higher prefetch lookahead value or lets the system set automatically based on the IO latency to improve performance with the LOAD statement.") :arrow_upper_right:

