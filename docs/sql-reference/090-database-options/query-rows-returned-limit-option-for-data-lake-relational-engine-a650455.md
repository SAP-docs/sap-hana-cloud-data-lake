<!-- loioa650455584f210159c3f92442a8d0946 -->

# QUERY\_ROWS\_RETURNED\_LIMIT Option for Data Lake Relational Engine

Sets the row threshold for rejecting queries based on estimated size of result set.



<a name="loioa650455584f210159c3f92442a8d0946__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa650455584f210159c3f92442a8d0946__section_zx3_g24_hrb"/>

## Syntax

```
QUERY_ROWS_RETURNED_LIMIT = <value>;
```



<a name="loioa650455584f210159c3f92442a8d0946__iq_refso_901"/>

## Allowed Values

Any integer



<a name="loioa650455584f210159c3f92442a8d0946__iq_refso_902"/>

## Default

0



<a name="loioa650455584f210159c3f92442a8d0946__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa650455584f210159c3f92442a8d0946__iq_refso_903"/>

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



<a name="loioa650455584f210159c3f92442a8d0946__iq_refso_904"/>

## Remarks

If data lake Relational Engine receives a query that has an estimated number of result rows greater than the value of QUERY\_ROWS\_RETURNED\_LIMIT, it rejects the query with this message:

```
Query rejected because it exceeds resource: Query_Rows_Returned_Limit
```

If you set this option to 0 \(the default\), there is no limit, and no queries are rejected based on the number of rows in their output.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

