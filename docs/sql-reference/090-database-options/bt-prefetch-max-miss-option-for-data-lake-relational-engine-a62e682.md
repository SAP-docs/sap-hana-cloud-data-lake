<!-- loioa62e682d84f21015a008a6f19e80fefe -->

# BT\_PREFETCH\_MAX\_MISS Option for Data Lake Relational Engine

Controls the way data lake Relational Engine determines whether to continue prefetching B-tree pages for a given query.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa62e682d84f21015a008a6f19e80fefe__section_xdr_2ry_brb"/>

## Syntax

```
BT_PREFETCH_MAX_MISS = <value>
```



<a name="loioa62e682d84f21015a008a6f19e80fefe__iq_refso_375"/>

## Allowed Values

0 to 1000



<a name="loioa62e682d84f21015a008a6f19e80fefe__iq_refso_376"/>

## Default

1



<a name="loioa62e682d84f21015a008a6f19e80fefe__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa62e682d84f21015a008a6f19e80fefe__iq_refso_377"/>

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



<a name="loioa62e682d84f21015a008a6f19e80fefe__iq_refso_378"/>

## Remarks

Use only if instructed to do so by SAP Technical Support. For queries that use HG \(High\_Group\) indexes, data lake Relational Engine prefetches B-tree pages sequentially until it determines that prefetching is no longer useful. For some queries, it might turn off prefetching prematurely. Increasing the value of BT\_PREFETCH\_MAX\_MISS makes it more likely that data lake Relational Engine continues prefetching, but might also increase I/O unnecessarily.

If queries using HG indexes run more slowly than expected, try gradually increasing the value of BT\_PREFETCH\_MAX\_MISS.

Experiment with different settings to find the setting that gives the best performance. For most queries, useful settings are in the range of 1 to 10.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[BT\_PREFETCH\_SIZE Option for Data Lake Relational Engine](bt-prefetch-size-option-for-data-lake-relational-engine-a62e965.md "Restricts the size of the read-ahead buffer for the High_Group B-tree.")

[PREFETCH\_BUFFER\_LIMIT Option for Data Lake Relational Engine](prefetch-buffer-limit-option-for-data-lake-relational-engine-a649b32.md "Specifies the amount of memory used for prefetching.")

