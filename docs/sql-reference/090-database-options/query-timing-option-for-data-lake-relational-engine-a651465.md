<!-- loioa651465684f2101589c5883a674a4cc0 -->

# QUERY\_TIMING Option for Data Lake Relational Engine

Determines whether or not to collect specific timing statistics and display them in the query plan.



<a name="loioa651465684f2101589c5883a674a4cc0__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa651465684f2101589c5883a674a4cc0__section_bmb_cgy_lrb"/>

## Syntax

```
QUERY_TIMING = { ON | OFF };
```



<a name="loioa651465684f2101589c5883a674a4cc0__iq_refso_909"/>

## Allowed Values

ON, OFF



<a name="loioa651465684f2101589c5883a674a4cc0__iq_refso_910"/>

## Default

ON



<a name="loioa651465684f2101589c5883a674a4cc0__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa651465684f2101589c5883a674a4cc0__iq_refso_911"/>

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



<a name="loioa651465684f2101589c5883a674a4cc0__iq_refso_912"/>

## Remarks

This option controls the collection of timing statistics on subqueries and some other repetitive functions in the query engine.

Query timing is represented in the query plan detail as a series of timestamps. These timestamps correspond to query operator phases \(Conditions, Prepare, Fetch, Complete\). HTML and Interactive SQL query plans display query timing graphically as a timeline.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

