<!-- loioa64d3bd284f21015aad0b675488e59f3 -->

# QUERY\_PLAN Option for Data Lake Relational Engine

Specifies whether or not additional query plans are printed to the data lake Relational Engine message file.



<a name="loioa64d3bd284f21015aad0b675488e59f3__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa64d3bd284f21015aad0b675488e59f3__section_dyc_zbt_lrb"/>

## Syntax

```
QUERY_PLAN = { ON | OFF };
```



<a name="loioa64d3bd284f21015aad0b675488e59f3__iq_refso_875"/>

## Allowed Values

ON, OFF



<a name="loioa64d3bd284f21015aad0b675488e59f3__iq_refso_876"/>

## Default

OFF



<a name="loioa64d3bd284f21015aad0b675488e59f3__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa64d3bd284f21015aad0b675488e59f3__iq_refso_877"/>

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



<a name="loioa64d3bd284f21015aad0b675488e59f3__iq_refso_878"/>

## Remarks

When this option is turned ON, data lake Relational Engine produces textual query plans in the IQ message file. These query plans display the query tree topography, as well as details about optimization and execution. When this option is turned OFF, those messages are suppressed. The information is sent to the <code><i class="varname">&lt;dbname&gt;</i>.iqmsg</code> file.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[QUERY\_DETAIL Option for Data Lake Relational Engine](query-detail-option-for-data-lake-relational-engine-a64c3ef.md "Specifies whether or not to include additional query information in the Query Detail section of the query plan.")

[QUERY\_PLAN\_AFTER\_RUN Option for Data Lake Relational Engine](query-plan-after-run-option-for-data-lake-relational-engine-a64dbdd.md "Prints the entire query plan after query execution is complete.")

[QUERY\_PLAN\_AS\_HTML Option for Data Lake Relational Engine](query-plan-as-html-option-for-data-lake-relational-engine-a64e45d.md "Generates graphical query plans in HTML format for viewing in a Web browser.")

