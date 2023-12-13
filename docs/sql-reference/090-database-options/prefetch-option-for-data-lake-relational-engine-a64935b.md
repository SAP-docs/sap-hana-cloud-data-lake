<!-- loioa64935be84f21015a966bef945d03815 -->

# PREFETCH Option for Data Lake Relational Engine

Allows you to turn fetching on or off or to use the ALWAYS value to prefetch the cursor results, even for SENSITIVE cursor types and for cursors that involve a proxy table.



<a name="loioa64935be84f21015a966bef945d03815__section_rkt_5pr_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa64935be84f21015a966bef945d03815__section_zx3_g24_hrb"/>

## Syntax

```
PREFETCH = <value>;
```



<a name="loioa64935be84f21015a966bef945d03815__iq_refso_842"/>

## Allowed Values

ON, OFF, ALWAYS



<a name="loioa64935be84f21015a966bef945d03815__iq_refso_843"/>

## Default

ALWAYS



<a name="loioa64935be84f21015a966bef945d03815__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa64935be84f21015a966bef945d03815__iq_refso_844"/>

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



<a name="loioa64935be84f21015a966bef945d03815__iq_refso_845"/>

## Remarks

For the catalog store only, PREFETCH controls whether rows are fetched to the client side before being made available to the client application. Fetching a number of rows at a time, even when the client application requests rows one at a time \(for example, when looping over the rows of a cursor\) minimizes response time and improves overall throughput by limiting the number of requests to the database.

The setting of PREFETCH is ignored by Open Client and JDBC connections, and for the IQ store.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

