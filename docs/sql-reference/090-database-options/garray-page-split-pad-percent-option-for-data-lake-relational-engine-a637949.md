<!-- loioa637949784f21015835f8ebf9b26d3dc -->

# GARRAY\_PAGE\_SPLIT\_PAD\_PERCENT Option for Data Lake Relational Engine

Determines per-page fill factor during page splits on the garray and specifies the percent of space on each HG garray page to reserve for future incremental inserts.



<a name="loioa637949784f21015835f8ebf9b26d3dc__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa637949784f21015835f8ebf9b26d3dc__section_zx3_g24_hrb"/>

## Syntax

```
GARRAY_PAGE_SPLIT_PAD_PERCENT = <value>;
```



<a name="loioa637949784f21015835f8ebf9b26d3dc__iq_refso_569"/>

## Allowed Values

0 to 100



<a name="loioa637949784f21015835f8ebf9b26d3dc__iq_refso_570"/>

## Default

25



<a name="loioa637949784f21015835f8ebf9b26d3dc__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa637949784f21015835f8ebf9b26d3dc__iq_refso_571"/>

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



<a name="loioa637949784f21015835f8ebf9b26d3dc__iq_refso_572"/>

## Remarks

Splits of a garray page try to leave that percentage empty. This space is used for rows added to new index groups.

An HG index can reserve storage at the page level that can be allocated to new groups when additional rows are inserted. Reserving space consumes additional space, but can help the performance of incremental inserts into the HG index.

If future plans include incremental inserts into an HG index, and the new rows do not have values that are already present in the index, a nonzero value for GARRAY\_PAGE\_SPLIT\_PAD\_PERCENT could improve incremental insert performance.

If you do not plan to incrementally update the index, you can reduce the values of this option to save storage space.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[GARRAY\_FILL\_FACTOR\_PERCENT Option for Data Lake Relational Engine](garray-fill-factor-percent-option-for-data-lake-relational-engine-a637325.md "Specifies the percent of space on each HG garray page to reserve for future incremental inserts into existing groups.")

