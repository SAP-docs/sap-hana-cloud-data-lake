<!-- loioa64e45dd84f21015ac0fcd5c96f8f9af -->

# QUERY\_PLAN\_AS\_HTML Option for Data Lake Relational Engine

Generates graphical query plans in HTML format for viewing in a Web browser.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa64e45dd84f21015ac0fcd5c96f8f9af__query_plan_as_html_syntax1"/>

## Syntax

```
QUERY_PLAN_AS_HTML = { ON | OFF }
```



<a name="loioa64e45dd84f21015ac0fcd5c96f8f9af__query_plan_as_html_values1"/>

## Allowed Values

ON, OFF



<a name="loioa64e45dd84f21015ac0fcd5c96f8f9af__query_plan_as_html_default1"/>

## Default

OFF



<a name="loioa64e45dd84f21015ac0fcd5c96f8f9af__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa64e45dd84f21015ac0fcd5c96f8f9af__query_plan_as_html_scope1"/>

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



<a name="loioa64e45dd84f21015ac0fcd5c96f8f9af__query_plan_as_html_remarks1"/>

## Remarks

When you set this option, also set the QUERY\_NAME option for each query, so you know which query is associated with the query plan.

Data lake Relational Engine writes the plans in the same directory as the `.iqmsg` file. Query plan file names follow these conventions: <code><i class="varname">&lt;user-name&gt;</i>_<i class="varname">&lt;query-name&gt;</i>_<i class="varname">&lt;server-type&gt;</i>_<i class="varname">&lt;server-number&gt;</i>_<i class="varname">&lt;YYYYMMDD_HHMMSS&gt;</i>_<i class="varname">&lt;query-number&gt;</i>_<i class="varname">&lt;fragment-number&gt;</i>.html</code>

For example, if the user HDLADMIN sets the temporary option QUERY\_NAME to 'Query\_1123', a file created on November 8, 2012, at exactly 8:30 a.m. is called `HDLADMIN_QUERY_1123_L_0__20121108_083000_4.html`. The date, time, and unique *<query-number\>* appended to the file name ensure that existing files are not overwritten. The *<server-type\>* parameter indicates whether the plan originates from a leader \(L\) or worker \(W\) node. The *<server-number\>* identifies the server where the plan originated when all html files are routed to a single directory.

Worker nodes generate an html file for each fragment executed by the worker, which can result in multiple html files from a single query. These files are identified by *<fragment-number\>*.

> ### Note:  
> If you use this feature, monitor your storagespace usage so you leave enough room for your `.iqmsg` and log files to grow. Enable IQ message log wrapping or message log archiving to avoid filling up your message log file.

QUERY\_PLAN\_AS\_HTML acts independently of the setting for the QUERY\_PLAN option. In other words, if QUERY\_PLAN\_AS\_HTML is ON, you get an HTML format query plan whether or not QUERY\_PLAN is ON.

This feature is supported with newer versions of many commonly used browsers. Some browsers might experience problems with plans generated for very complicated queries.



## Examples



Output generated from a query plan named Q101. The leader node \(L\) *<query-number\>* is 1; worker \(W\) nodes are numbered 2 and 3. Notice the *<fragment-number\>* that appears after the query number in the worker output.

Output generated from the leader node:

```
HDLADMIN_L_1_Q101_20121108_083000_94.html
```

Output from one of the worker nodes:

```
HDLADMIN_W_2_Q101_20121108_083000_94_2.html
HDLADMIN_W_2_Q101_20121108_083000_94_1.html
```

Corresponding output from another worker:

```
HDLADMIN_W_3_Q101_20121113-054928_94_2.html
HDLADMIN_W_3_Q101_20121113-054933_94_1.html
```

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[QUERY_PLAN_AS_HTML Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/486458ad1942418e9d70db482284c485.html "Generates graphical query plans in HTML format for viewing in a Web browser.") :arrow_upper_right:

[QUERY\_NAME Option for Data Lake Relational Engine](query-name-option-for-data-lake-relational-engine-a64cbce.md "Gives a name to an executed query in its query plan.")

[QUERY\_PLAN Option for Data Lake Relational Engine](query-plan-option-for-data-lake-relational-engine-a64d3bd.md "Specifies whether or not additional query plans are printed to the data lake Relational Engine message file.")

[QUERY\_PLAN\_AFTER\_RUN Option for Data Lake Relational Engine](query-plan-after-run-option-for-data-lake-relational-engine-a64dbdd.md "Prints the entire query plan after query execution is complete.")

