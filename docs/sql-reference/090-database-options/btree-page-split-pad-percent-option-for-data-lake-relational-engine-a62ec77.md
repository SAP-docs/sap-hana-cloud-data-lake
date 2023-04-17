<!-- loioa62ec77884f210158d70ac1c0c792ba6 -->

# BTREE\_PAGE\_SPLIT\_PAD\_PERCENT Option for Data Lake Relational Engine

Determines per-page fill factor during page splits for B-tree structures.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa62ec77884f210158d70ac1c0c792ba6__section_ukt_bry_brb"/>

## Syntax

```
BTREE_PAGE_SPLIT_PAD_PERCENT = <value>
```



<a name="loioa62ec77884f210158d70ac1c0c792ba6__iq_refso_384"/>

## Allowed Values

0 to 90



<a name="loioa62ec77884f210158d70ac1c0c792ba6__iq_refso_385"/>

## Default

50



<a name="loioa62ec77884f210158d70ac1c0c792ba6__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa62ec77884f210158d70ac1c0c792ba6__iq_refso_386"/>

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



<a name="loioa62ec77884f210158d70ac1c0c792ba6__iq_refso_387"/>

## Remarks

B-tree structures are used by the HG, DT, TIME, and DTTM indexes. Splits of a B-tree page try to leave the specified percentage empty to avoid splitting when new keys are inserted into the index.

Indexes reserve storage at the page level that can be allocated to new keys as additional data is inserted. Reserving space consumes additional storage space, but can help the performance of incremental inserts. If future plans include incremental inserts, and the new rows do not have values that are already present in the index, a nonzero value for GARRAY\_PAGE\_SPLIT\_PAD\_PERCENT may improve incremental insert performance.

If you do not plan to incrementally update the index, you can reduce the value of this option to save storage space.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[GARRAY\_FILL\_FACTOR\_PERCENT Option for Data Lake Relational Engine](garray-fill-factor-percent-option-for-data-lake-relational-engine-a637325.md "Specifies the percent of space on each HG garray page to reserve for future incremental inserts into existing groups.")

[GARRAY\_PAGE\_SPLIT\_PAD\_PERCENT Option for Data Lake Relational Engine](garray-page-split-pad-percent-option-for-data-lake-relational-engine-a637949.md "Determines per-page fill factor during page splits on the garray and specifies the percent of space on each HG garray page to reserve for future incremental inserts.")

[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

