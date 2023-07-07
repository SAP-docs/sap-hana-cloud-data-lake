<!-- loioa64f443284f21015acbbd8e919d9c49b -->

# QUERY\_PLAN\_TEXT\_ACCESS Option for Data Lake Relational Engine

Enables or prevents users from accessing query plans from the Interactive SQL client or from using SQL functions to get plans.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa64f443284f21015acbbd8e919d9c49b__query_plan_text_access_syntax1"/>

## Syntax

```
QUERY_PLAN_TEXT_ACCESS = { ON | OFF }
```



<a name="loioa64f443284f21015acbbd8e919d9c49b__query_plan_text_access_values1"/>

## Allowed Values

ON, OFF



<a name="loioa64f443284f21015acbbd8e919d9c49b__query_plan_text_access_default1"/>

## Default

OFF



<a name="loioa64f443284f21015acbbd8e919d9c49b__query_plan_text_access_priv1"/>

## Privileges

Privilege Category: SYSTEM



### 

Requires the SET ANY CUSTOMER SYSTEM OPTION system privilege to set this database option.



<a name="loioa64f443284f21015acbbd8e919d9c49b__query_plan_text_access_scope1"/>

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



<a name="loioa64f443284f21015acbbd8e919d9c49b__query_plan_text_access_remarks1"/>

## Remarks

When QUERY\_PLAN\_TEXT\_ACCESS option is ON, users can view, save, and print query plans from the Interactive SQL client. When the option is OFF, query plans are not cached, and other query plan-related database options have no effect on the query plan that is shown from the Interactive SQL client. This error message appears:

```
No plan available. The database option QUERY_PLAN_TEXT_ACCESS is OFF.
```

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[QUERY_PLAN_TEXT_ACCESS Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/176630977a7d4a46b04fe1f7b30fd9c2.html "Enables or prevents users from accessing query plans from the Interactive SQL client or from using SQL functions to get plans.") :arrow_upper_right:

[QUERY\_DETAIL Option for Data Lake Relational Engine](query-detail-option-for-data-lake-relational-engine-a64c3ef.md "Specifies whether or not to include additional query information in the Query Detail section of the query plan.")

[QUERY\_PLAN\_AFTER\_RUN Option for Data Lake Relational Engine](query-plan-after-run-option-for-data-lake-relational-engine-a64dbdd.md "Prints the entire query plan after query execution is complete.")

[QUERY\_PLAN\_AS\_HTML Option for Data Lake Relational Engine](query-plan-as-html-option-for-data-lake-relational-engine-a64e45d.md "Generates graphical query plans in HTML format for viewing in a Web browser.")

[QUERY\_PLAN\_TEXT\_CACHING Option for Data Lake Relational Engine](query-plan-text-caching-option-for-data-lake-relational-engine-a64fc89.md "Allows you to specify whether or not data lake Relational Engine generates and caches IQ plans for queries executed by the user.")

[OUTPUT Statement \[Interactive SQL\] for Data Lake Relational Engine](../080-sql-statements/output-statement-interactive-sql-for-data-lake-relational-engine-a62189f.md "Writes the information retrieved by the current query to a file.")

