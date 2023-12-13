<!-- loioa64fc89984f210159c879335f5b3713d -->

# QUERY\_PLAN\_TEXT\_CACHING Option for Data Lake Relational Engine

Allows you to specify whether or not data lake Relational Engine generates and caches IQ plans for queries executed by the user.



<a name="loioa64fc89984f210159c879335f5b3713d__section_fq2_gpq_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa64fc89984f210159c879335f5b3713d__query_plan_text_caching_syntax1"/>

## Syntax

```
QUERY_PLAN_TEXT_CACHING = { ON | OFF };
```



<a name="loioa64fc89984f210159c879335f5b3713d__query_plan_text_caching_values1"/>

## Allowed Values

ON, OFF



<a name="loioa64fc89984f210159c879335f5b3713d__query_plan_text_caching_default1"/>

## Default

OFF



<a name="loioa64fc89984f210159c879335f5b3713d__query_plan_text_caching_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa64fc89984f210159c879335f5b3713d__query_plan_text_caching_scope1"/>

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



<a name="loioa64fc89984f210159c879335f5b3713d__query_plan_text_caching_remarks1"/>

## Remarks

IQ query plans vary in size and can become very large for complex queries. Caching plans for display on the Interactive SQL client can have high resource requirements. The QUERY\_PLAN\_TEXT\_CACHING option gives users a mechanism to control resources for caching plans. With this option turned OFF \(the default\), the query plan is not cached for that user connection.

> ### Note:  
> If QUERY\_PLAN\_TEXT\_ACCESS is turned OFF, the query plan is not cached for the connections from that user, no matter how QUERY\_PLAN\_TEXT\_CACHING is set.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[QUERY_PLAN_TEXT_CACHING Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/bee56c43ec8243e5a5771609c43248e2.html "Allows you to specify whether or not data lake Relational Engine generates and caches IQ plans for queries executed by the user.") :arrow_upper_right:

