<!-- loioa62bf97e84f21015843682381c2172d5 -->

# AGGREGATION\_PREFERENCE Option for Data Lake Relational Engine

Controls the choice of algorithms for processing an aggregate.



<a name="loioa62bf97e84f21015843682381c2172d5__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa62bf97e84f21015843682381c2172d5__section_u1n_l5b_qkb"/>

## Syntax

```
AGGREGATION_PREFERENCE = <number_expression>;
```



<a name="loioa62bf97e84f21015843682381c2172d5__iq_refso_323"/>

## Allowed Values

\-6 to 6

-   0 – lets the optimizer choose.
-   1 – prefers aggregation with a sort.
-   2 – prefers aggregation using IQ indexes.
-   3 – prefers aggregation with a hash.
-   4 – prefers aggregation with a distinct/grouping sort.
-   5 – prefers aggregation with a sort if grouping columns include all the partitioning keys of a hash partitioned table.
-   6 – prefers aggregation with a hash if grouping columns include all the partitioning keys of a hash partitioned table.
-   \-1 – avoids aggregation with a sort.
-   \-2 – avoids aggregation using IQ indexes.
-   \-3 – avoids aggregation with a hash.
-   \-4 – avoids aggregation with a distinct/grouping sort.
-   \-5 – avoids aggregation with a sort if grouping columns include all the partitioning keys of a hash partitioned table.
-   \-6 – avoids aggregation with a hash if grouping columns include all the partitioning keys of a hash partitioned table.



<a name="loioa62bf97e84f21015843682381c2172d5__iq_refso_324"/>

## Default

0



<a name="loioa62bf97e84f21015843682381c2172d5__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa62bf97e84f21015843682381c2172d5__iq_refso_325"/>

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



<a name="loioa62bf97e84f21015843682381c2172d5__iq_refso_326"/>

## Remarks

For aggregation \(GROUP BY, DISTINCT, SET functions\) within a query, the data lake Relational Engine optimizer has a choice of several algorithms for processing the aggregate. AGGREGATION\_PREFERENCE lets you override the costing decision of the optimizer when choosing the algorithm. the option does not override internal rules that determine whether an algorithm is legal within the query engine.

This option is normally used for internal testing and for manually tuning queries that the optimizer does not handle well. Only experienced DBAs should use it. Inform SAP Technical Support, if you need to set AGGREGATION\_PREFERENCE, as setting this option might mean that a change to the optimizer may be appropriate.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

