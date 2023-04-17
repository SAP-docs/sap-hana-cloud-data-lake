<!-- loioa64dbdd384f21015983ac21e25acaab1 -->

# QUERY\_PLAN\_AFTER\_RUN Option for Data Lake Relational Engine

Prints the entire query plan after query execution is complete.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa64dbdd384f21015983ac21e25acaab1__query_plan_after_run_syntax1"/>

## Syntax

```
QUERY_PLAN_AFTER_RUN = { ON | OFF }
```



<a name="loioa64dbdd384f21015983ac21e25acaab1__query_plan_after_run_values1"/>

## Allowed Values

ON, OFF



<a name="loioa64dbdd384f21015983ac21e25acaab1__query_plan_after_run_default1"/>

## Default

ON



<a name="loioa64dbdd384f21015983ac21e25acaab1__query_plan_after_run_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa64dbdd384f21015983ac21e25acaab1__query_plan_after_run_scope1"/>

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



<a name="loioa64dbdd384f21015983ac21e25acaab1__iq_refso_882"/>

## Remarks

When QUERY\_PLAN\_AFTER\_RUN is turned ON, the query plan is printed after the query has finished running. This allows the query plan to include additional information, such as the actual number of rows passed on from each node of the query.

For this option to work, the QUERY\_PLAN option must be set to ON. You can use this option in conjunction with QUERY\_DETAIL to generate additional information in the query plan report.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[QUERY_PLAN_AFTER_RUN Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/60575248dc354201b6191e03d24b21fc.html "Prints the entire query plan after query execution is complete.") :arrow_upper_right:

[QUERY\_DETAIL Option for Data Lake Relational Engine](query-detail-option-for-data-lake-relational-engine-a64c3ef.md "Specifies whether or not to include additional query information in the Query Detail section of the query plan.")

[QUERY\_PLAN Option for Data Lake Relational Engine](query-plan-option-for-data-lake-relational-engine-a64d3bd.md "Specifies whether or not additional query plans are printed to the data lake Relational Engine message file.")

[QUERY\_PLAN\_AS\_HTML Option for Data Lake Relational Engine](query-plan-as-html-option-for-data-lake-relational-engine-a64e45d.md "Generates graphical query plans in HTML format for viewing in a Web browser.")

