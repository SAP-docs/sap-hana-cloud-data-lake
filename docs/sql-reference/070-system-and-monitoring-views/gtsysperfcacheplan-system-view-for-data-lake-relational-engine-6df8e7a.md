<!-- loio6df8e7a30fda4bca914f4c1f9b5b574e -->

# GTSYSPERFCACHEPLAN System View for Data Lake Relational Engine

Each row in the GTSYSPERFCACHEPLAN system view contains a graphical plan string for an execution plan of the specified statement.



> ### Restriction:  
> This data lake Relational Engine system view can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




<table>
<tr>
<th valign="top">

Column name



</th>
<th valign="top">

Data type



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

stmt\_hash



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

Unique identifier assigned to each query.



</td>
</tr>
<tr>
<td valign="top">

plan\_hash



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

ID assigned to each plan for a given statement.



</td>
</tr>
<tr>
<td valign="top">

plan\_text



</td>
<td valign="top">

XML NOT NULL



</td>
<td valign="top">

XML representation of the query execution plan.



</td>
</tr>
<tr>
<td valign="top">

update



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

The time the statement was executed. This value is Coordinated Universal Time \(UTC\) time.



</td>
</tr>
</table>



## Remarks

Provides an XML representation of the query execution plan for certain expensive statements.

Plans aren't recorded for statements with execution times less than the QUERY\_PLAN\_MIN\_TIME threshold.

> ### Note:  
> The GTSYSPERFCACHEPLAN system view returns a query execution plan in XML format similar to plans in the `dbisql` *Plan Viewer* tab. It doesn't return query plans in HTML format.
> 
> To minimize performance degradation, data lake Relational Engine records plan information in GTSYSPERFCACHEPLAN only when the statement performance monitoring algorithm determines the query is expensive enough to warrant monitoring. Therefore, not all expensive statements show in GTSYSPERFCACHEPLAN. Moreover, not all expensive statements of interest showing in the GTSYSPERFCACHESTMT system view show a corresponding plan in GTSYSPERFCACHEPLAN, since writing to GTSYSPERFCACHESTMT has a smaller impact on performance.
> 
> A statement may not show in GTSYSPERFCACHEPLAN until it executes a second time, or until the performance buffer gets purged to disk. If server workload is high, an expensive statement may not show in GTSYSPERFCACHEPLAN at all.
> 
> A statement with an execution time exceeding the QUERY\_PLAN\_MIN\_TIME threshold may not show in GTSYSPERFCACHEPLAN. The QUERY\_PLAN\_MIN\_TIME threshold helps the statement performance monitoring algorithm identify expensive outliers, but doesn’t guarantee that every statement violating the threshold gets recorded.
> 
> Plans for internal statements appear in the view.



## Privileges

You must have the SELECT privilege on the view to use this view.

**Related Information**  


[Monitoring Statement Performance in Data Lake Relational Engine](https://help.sap.com/viewer/a8982cc084f21015a7b4b7fcdeb0953d/2023_1_QRC/en-US/a50746e62c2248c2a66f34c8e34fb722.html "The statement performance monitoring feature is not an exhaustive, complete audit of slow SQL statements (queries), but it is a useful tool for providing an approximation, or high-level summary, of query workload. Statement performance monitoring flags certain outlier statements with execution times exceeding an established baseline.") :arrow_upper_right:

[GRANT Object-Level Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md "Grants database object-level privileges on individual objects and schemas to a user or role.")

[GTSYSPERFCACHESTMT System View for Data Lake Relational Engine](gtsysperfcachestmt-system-view-for-data-lake-relational-engine-7c163a0.md "Each row in the GTSYSPERFCACHESTMT system view represents SQL text for a statement with the constants removed.")

