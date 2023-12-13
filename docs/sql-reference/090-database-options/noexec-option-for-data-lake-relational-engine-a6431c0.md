<!-- loioa6431c0e84f21015877cc254cbee3e05 -->

# NOEXEC Option for Data Lake Relational Engine

Generates the optimizer query plans instead of executing the plan.



<a name="loioa6431c0e84f21015877cc254cbee3e05__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa6431c0e84f21015877cc254cbee3e05__section_ytq_1xs_lrb"/>

## Syntax

```
NOEXEC = { ON | OFF };
```



<a name="loioa6431c0e84f21015877cc254cbee3e05__iq_refso_794"/>

## Allowed Values

ON, OFF



<a name="loioa6431c0e84f21015877cc254cbee3e05__iq_refso_795"/>

## Default

OFF



<a name="loioa6431c0e84f21015877cc254cbee3e05__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa6431c0e84f21015877cc254cbee3e05__iq_refso_796"/>

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



<a name="loioa6431c0e84f21015877cc254cbee3e05__iq_refso_797"/>

## Remarks

When determining how to process a query, the IQ optimizer generates a query plan to map how it plans to have the query engine process the query. If this option is set ON, the optimizer sends the plan for the query to the IQ message file rather than submitting it to the query engine. NOEXEC affects queries and commands that include a query.

Setting NOEXEC ON also prevents the execution of INSERT...VALUES, INSERT...SELECT, INSERT...LOCATION, SELECT...INTO, LOAD TABLE, UPDATE, TRUNCATE TABLE, DELETE, and updatable cursor operations.

When the EARLY\_PREDICATE\_EXECUTION option is ON, data lake Relational Engine executes the local predicates for all queries before generating a query plan, even when the NOEXEC option is ON. The generated query plan is the same as the runtime plan.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[EARLY\_PREDICATE\_EXECUTION Option for Data Lake Relational Engine](early-predicate-execution-option-for-data-lake-relational-engine-a635846.md "Controls whether simple local predicates are executed before query optimization.")

