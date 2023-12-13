<!-- loioa63bb2e884f210158490d70844b57a75 -->

# JOIN\_PREFERENCE Option for Data Lake Relational Engine

Controls the choice of algorithms when processing joins.



<a name="loioa63bb2e884f210158490d70844b57a75__section_yxs_mkr_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa63bb2e884f210158490d70844b57a75__section_zx3_g24_hrb"/>

## Syntax

```
JOIN_PREFERENCE = <value>;
```



<a name="loioa63bb2e884f210158490d70844b57a75__iq_refso_667"/>

## Allowed Values

-   0 – lets the optimizer choose
-   1 – prefers sort-merge
-   2 – prefers nested-loop
-   3 – prefers nested-loop push-down
-   4 – prefers hash
-   5 – prefers hash push-down
-   6 – prefers asymmetric sort-merge join
-   7 – prefers sort-merge push-down
-   8 – prefers asymmetric sort-merge push-down join
-   9 – prefers partitioned hash join if the join keys include all the partition keys of a hash partitioned table
-   10 – prefers partitioned hash-push down join if the join keys include all the partition keys of a hash partitioned table
-   11 – prefers partitioned sort-merge join if the join keys include all the partition keys of a hash partitioned table
-   12 – prefers partitioned sort-merge push-down join if the join keys include all the partition keys of a hash partitioned table
-   \-1 – avoids sort-merge
-   \-2 – avoids nested-loop
-   \-3 – avoids nested-loop push-down
-   \-4 – avoids hash
-   \-5 – avoids hash push-down
-   \-6 – avoids asymmetric sort-merge join
-   \-7 – avoids sort-merge push-down
-   \-8 – avoids asymmetric sort-merge push-down join
-   \-9 – avoids partitioned hash join if the join keys include all the partition keys of a hash partitioned table
-   \-10 – avoids partitioned hash-push down join if the join keys include all the partition keys of a hash partitioned table
-   \-11 – avoids partitioned sort-merge join if the join keys include all the partition keys of a hash partitioned table
-   \-12 – avoids partitioned sort-merge push-down join if the join keys include all the partition keys of a hash partitioned table



<a name="loioa63bb2e884f210158490d70844b57a75__iq_refso_668"/>

## Default

0



<a name="loioa63bb2e884f210158490d70844b57a75__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa63bb2e884f210158490d70844b57a75__iq_refso_669"/>

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



<a name="loioa63bb2e884f210158490d70844b57a75__iq_refso_670"/>

## Remarks

For joins within a query, the data lake Relational Engine optimizer has a choice of several algorithms for processing the join. JOIN\_PREFERENCE allows you to override the optimizer’s cost-based decision when choosing the algorithm to use. It does not override internal rules that determine whether an algorithm is legal within the query engine. If you set it to any nonzero value, every join in a query is affected; you cannot use it to selectively modify one join out of several in a query, but join condition hint strings can do so.

This option is normally used for internal testing or tuning of report queries, and only experienced DBAs should use it.

Simple equality join predicates can be tagged with a predicate hint that allows a join preference to be specified for just that one join. If the same join has more than one join condition with a local join preference, and if those hints are not the same value, then all local preferences are ignored for that join. Local join preferences do not affect the join order chosen by the optimizer

This example requests a hash join:

```
AND (T.X = 10 * R.x, 'J:4');
```

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

