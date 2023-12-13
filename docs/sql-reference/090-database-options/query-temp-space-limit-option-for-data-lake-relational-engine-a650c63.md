<!-- loioa650c63284f21015ae2f84afde7fb328 -->

# QUERY\_TEMP\_SPACE\_LIMIT Option for Data Lake Relational Engine

Specifies the maximum estimated amount of temp space before a query is rejected.



<a name="loioa650c63284f21015ae2f84afde7fb328__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa650c63284f21015ae2f84afde7fb328__section_zx3_g24_hrb"/>

## Syntax

```
QUERY_TEMP_SPACE_LIMIT = <value>;
```



<a name="loioa650c63284f21015ae2f84afde7fb328__iq_refso_905"/>

## Allowed Values

Any integer



<a name="loioa650c63284f21015ae2f84afde7fb328__iq_refso_906"/>

## Default

0 \(no limit\)



<a name="loioa650c63284f21015ae2f84afde7fb328__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa650c63284f21015ae2f84afde7fb328__iq_refso_907"/>

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



<a name="loioa650c63284f21015ae2f84afde7fb328__iq_refso_908"/>

## Remarks

If data lake Relational Engine receives a query that is estimated to require a temporary result space larger than value of this option, it rejects the query with this message:

```
Query rejected because it exceeds total space resource limit
```

When set to 0 \(the default\), there is no limit on temporary store usage by queries.

Users may override this option in their own environments to run queries that can potentially fill up the entire temporary store. To prevent runaway queries from filling up the temporary store, a user with the SET ANY CUSTOMER SYSTEM OPTION system privilege can set the option MAX\_TEMP\_SPACE\_PER\_CONNECTION. The MAX\_TEMP\_SPACE\_PER\_CONNECTION option monitors and limits actual temporary store usage for all DML statements, not just queries.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[MAX\_TEMP\_SPACE\_PER\_CONNECTION Option for Data Lake Relational Engine](max-temp-space-per-connection-option-for-data-lake-relational-engine-a640929.md "Limits temporary store space used per connection.")

