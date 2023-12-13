<!-- loioa637325784f2101595b1f18ba87c93e4 -->

# GARRAY\_FILL\_FACTOR\_PERCENT Option for Data Lake Relational Engine

Specifies the percent of space on each HG garray page to reserve for future incremental inserts into existing groups.



<a name="loioa637325784f2101595b1f18ba87c93e4__section_rwc_fhr_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa637325784f2101595b1f18ba87c93e4__section_zx3_g24_hrb"/>

## Syntax

```
GARRAY_FILL_FACTOR_PERCENT = <value>;
```



<a name="loioa637325784f2101595b1f18ba87c93e4__iq_refso_561"/>

## Allowed Values

0 to 1000



<a name="loioa637325784f2101595b1f18ba87c93e4__iq_refso_562"/>

## Default

25



<a name="loioa637325784f2101595b1f18ba87c93e4__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa637325784f2101595b1f18ba87c93e4__iq_refso_563"/>

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



<a name="loioa637325784f2101595b1f18ba87c93e4__iq_refso_564"/>

## Remarks

The garray tries to pad out each group to include a pad of empty space set by the value. This space is used for rows added to existing index groups.

An HG index can reserve some storage on a per-group basis \(where group is defined as a group of rows with equivalent values\). Reserving space consumes additional storagespace, but can help the performance of incremental inserts into the HG index.

If you plan to do future incremental inserts into an HG index, and those new rows have values that are already present in the index, a nonzero value for this option might improve incremental insert performance.

If you do not plan to incrementally update the index, you can reduce the values of this option to save space.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[GARRAY\_PAGE\_SPLIT\_PAD\_PERCENT Option for Data Lake Relational Engine](garray-page-split-pad-percent-option-for-data-lake-relational-engine-a637949.md "Determines per-page fill factor during page splits on the garray and specifies the percent of space on each HG garray page to reserve for future incremental inserts.")

[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

