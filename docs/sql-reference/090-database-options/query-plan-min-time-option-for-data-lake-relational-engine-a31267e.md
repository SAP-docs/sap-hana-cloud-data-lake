<!-- loioa31267e384f210158cfeeef7b6d1a826 -->

# QUERY\_PLAN\_MIN\_TIME Option for Data Lake Relational Engine

Specifies a threshold for query execution. The post-query plan is generated only if the query execution time exceeds the threshold.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa31267e384f210158cfeeef7b6d1a826__section_zx3_g24_hrb"/>

## Syntax

```
QUERY_PLAN_MIN_TIME = <value>
```



## Allowed Values

Integer, in milliseconds.



## Default

0



<a name="loioa31267e384f210158cfeeef7b6d1a826__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



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



## Remarks

A query with a very short execution time \(a micro query\) executes faster if a query plan is not generated. Setting this option avoids the generation of query plans, and the associated query plan generation costs for these queries. The QUERY\_PLAN\_MIN\_TIME option is ignored unless the following options are also set:

-   QUERY\_PLAN = ON or QUERY\_PLAN\_AS\_HTML = ON
-   QUERY\_PLAN\_AFTER\_RUN = ON
-   QUERY\_TIMING = ON

When these options are set, setting a QUERY\_PLAN\_MIN\_TIME query execution threshold prevents the generation of query plans for queries with execution times that do not exceed the specified threshold.

If using the statement performance monitoring feature \(that is, you set the COLLECT\_IQ\_PERFORMANCE option to ON\), QUERY\_PLAN\_MIN\_TIME specifies the reporting threshold for consideration by the performance monitoring algorithm. Only those SQL statements with execution times exceeding this threshold will be considered.

> ### Note:  
> Not all queries with execution times exceeding the QUERY\_PLAN\_MIN\_TIME threshold are considered by the statement performance monitoring algorithm; therefore the query details, XML query plan, and SQL query text may not be recorded. The QUERY\_PLAN\_MIN\_TIME threshold helps the statement performance monitoring algorithm identify expensive outliers, but does not guarantee that every statement violating the threshold gets recorded.
> 
> Query plan and query text is recorded only if the algorithm determines the query is expensive enough to warrant monitoring.
> 
> There may be a delay between query execution, and when query plan and query text information displays in the GTSYSPERFCACHEPLAN and GTSYSPERFCACHESTMT system views.
> 
> Moreover, query plan, query text, and runtime query information for a particular statement may not be recorded at all due to performance considerations. Statement performance monitoring only maintains information for up to 10,000 statements. If workload is high, this buffer may be full and some slow statements may not be monitored – even if they are slow statements of interest.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[GTSYSPERFCACHEPLAN System View for Data Lake Relational Engine](../070-system-and-monitoring-views/gtsysperfcacheplan-system-view-for-data-lake-relational-engine-6df8e7a.md "Each row in the GTSYSPERFCACHEPLAN system view contains a graphical plan string for an execution plan of the specified statement.")

[GTSYSPERFCACHESTMT System View for Data Lake Relational Engine](../070-system-and-monitoring-views/gtsysperfcachestmt-system-view-for-data-lake-relational-engine-7c163a0.md "Each row in the GTSYSPERFCACHESTMT system view represents SQL text for a statement with the constants removed.")

