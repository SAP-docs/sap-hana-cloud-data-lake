<!-- loio7c163a0aa89641c59d30b07ffecd9bd3 -->

# GTSYSPERFCACHESTMT System View for Data Lake Relational Engine

Each row in the GTSYSPERFCACHESTMT system view represents SQL text for a statement with the constants removed.



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

A unique identifier assigned to each statement.



</td>
</tr>
<tr>
<td valign="top">

stmt\_text



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

SQL representation of the statement.



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

The statement performance summary feature uses the SQL statement stored in this view.

> ### Note:  
> To minimize performance degradation, data lake Relational Engine records statement SQL text in GTSYSPERFCACHESTMT only when the statement performance monitoring algorithm determines the query is expensive enough to warrant monitoring. Therefore, not all expensive statements show in GTSYSPERFCACHESTMT. Moreover, not all expensive statements of interest showing in the GTSYSPERFCACHESTMT system view show a corresponding plan in GTSYSPERFCACHEPLAN, since writing to GTSYSPERFCACHESTMT has a smaller impact on performance.
> 
> A statement may not show in GTSYSPERFCACHESTMT until it executes a second time, or until the performance buffer gets purged to disk. If server workload is high, an expensive statement may not show in GTSYSPERFCACHESTMT at all.
> 
> A statement with an execution time exceeding the QUERY\_PLAN\_MIN\_TIME threshold may not show in GTSYSPERFCACHESTMT. The QUERY\_PLAN\_MIN\_TIME threshold helps the statement performance monitoring algorithm identify expensive outliers, but does not guarantee that every statement violating the threshold gets recorded.
> 
> Internal statements appear in the view.



<a name="loio7c163a0aa89641c59d30b07ffecd9bd3__section_ph4_dk4_ktb"/>

## Privileges

You must have the SELECT privilege on the view to use this view.

**Related Information**  


[GRANT Object-Level Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md "Grants database object-level privileges on individual objects and schemas to a user or role.")

[Monitoring Statement Performance in Data Lake Relational Engine](https://help.sap.com/viewer/a8982cc084f21015a7b4b7fcdeb0953d/2023_2_QRC/en-US/a50746e62c2248c2a66f34c8e34fb722.html "The statement performance monitoring feature is not an exhaustive, complete audit of slow SQL statements (queries), but it is a useful tool for providing an approximation, or high-level summary, of query workload. Statement performance monitoring flags certain outlier statements with execution times exceeding an established baseline.") :arrow_upper_right:

[GTSYSPERFCACHEPLAN System View for Data Lake Relational Engine](gtsysperfcacheplan-system-view-for-data-lake-relational-engine-6df8e7a.md "Each row in the GTSYSPERFCACHEPLAN system view contains a graphical plan string for an execution plan of the specified statement.")

