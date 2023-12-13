<!-- loioa64c3ef384f21015ac76f94d8db150c5 -->

# QUERY\_DETAIL Option for Data Lake Relational Engine

Specifies whether or not to include additional query information in the Query Detail section of the query plan.



<a name="loioa64c3ef384f21015ac76f94d8db150c5__section_fq2_gpq_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa64c3ef384f21015ac76f94d8db150c5__query_detail_syntax1"/>

## Syntax

```
QUERY_DETAIL = { ON | OFF };
```



<a name="loioa64c3ef384f21015ac76f94d8db150c5__query_detail_values1"/>

## Allowed Values

ON, OFF



<a name="loioa64c3ef384f21015ac76f94d8db150c5__query_detail_default1"/>

## Default

ON



<a name="loioa64c3ef384f21015ac76f94d8db150c5__query_detail_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa64c3ef384f21015ac76f94d8db150c5__query_detail_scope1"/>

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



<a name="loioa64c3ef384f21015ac76f94d8db150c5__query_detail_remarks1"/>

## Remarks

When QUERY\_DETAIL and QUERY\_PLAN \(or QUERY\_PLAN\_AS\_HTML\) are both turned on, data lake Relational Engine displays additional information about the query when producing its query plan. When QUERY\_PLAN and QUERY\_PLAN\_AS\_HTML are OFF, this option is ignored.

When QUERY\_PLAN is ON \(the default\), especially if QUERY\_DETAIL is also ON, you might want to enable message log wrapping or message log archiving to avoid filling up your message log file.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[QUERY_DETAIL Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/4aa5427fd7c64273ae3b7d06a5c33ce8.html "Specifies whether or not to include additional query information in the Query Detail section of the query plan.") :arrow_upper_right:

[QUERY\_PLAN Option for Data Lake Relational Engine](query-plan-option-for-data-lake-relational-engine-a64d3bd.md "Specifies whether or not additional query plans are printed to the data lake Relational Engine message file.")

[QUERY\_PLAN\_AS\_HTML Option for Data Lake Relational Engine](query-plan-as-html-option-for-data-lake-relational-engine-a64e45d.md "Generates graphical query plans in HTML format for viewing in a Web browser.")

