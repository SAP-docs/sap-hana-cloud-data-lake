<!-- loioe68301094c2549b2822e9cdbcb84dfb6 -->

# iqmonThreadManager System View for Data Lake Relational Engine

A resource-level monitoring view for troubleshooting performance issues. iqmonThreadManager provides information about the resources managed by the thread manager, including thread pool size, available threads, and number of thread teams.



> ### Restriction:  
> This data lake Relational Engine system view can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.


<table>
<tr>
<th valign="top">

Column Name



</th>
<th valign="top">

Data Type



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

ThreadPoolSize



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The number of threads in the thread pool.



</td>
</tr>
<tr>
<td valign="top">

ThreadsFree



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The current number of free threads. This value is also available in [sp\_iqstatistics Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqstatistics-procedure-for-data-lake-relational-engine-a5b7d32.md) output.



</td>
</tr>
<tr>
<td valign="top">

ThreadsInUse



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The current number of active threads. This value is also available in [sp\_iqstatistics Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqstatistics-procedure-for-data-lake-relational-engine-a5b7d32.md) output.



</td>
</tr>
<tr>
<td valign="top">

ThreadTeamsInUse



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The current number of active thread teams.



</td>
</tr>
<tr>
<td valign="top">

MaxThreadTeams



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The maximum number of thread teams used since data lake Relational Engine server start.



</td>
</tr>
</table>



<a name="loioe68301094c2549b2822e9cdbcb84dfb6__section_kpt_vmz_1fb"/>

## Privileges

You must have the MONITOR system privilege to access this view. DBAs can consult [Granting a System Privilege to a User](https://help.sap.com/viewer/745778e524f74bb4af87460cca5e62c4/2023_2_QRC/en-US/a43bcb8284f210158039b1793a92a4fc.html "Allow the granting of specific system privileges to specific users, with or without administrative rights.") :arrow_upper_right: and [Alphabetical List of System Privileges for Data Lake Relational Engine](../080-sql-statements/alphabetical-list-of-system-privileges-for-data-lake-relational-engine-a449325.md) for information on granting the MONITOR system privilege to a user.



<a name="loioe68301094c2549b2822e9cdbcb84dfb6__section_ahv_5mg_bfb"/>

## Use Cases

Use iqmonThreadManager for diagnostic use-cases including:

-   Determining whether the thread pool size is sufficient by evaluating the thread use high-water mark, or the number of thread request rejections.

-   Monitoring thread pool use by periodically checking the free threads, and threads in use.


iqmonThreadManager, in conjunction with the other monitoring views, can help you troubleshoot common data lake Relational Engine performance problems. For diagnostic use-case information, see the [SAP HANA Cloud, Data Lake Performance and Tuning for Data Lake Relational Engine (Monitoring Views)](https://help.sap.com/viewer/028be133f34c4d2d998c6fbc258659c5/2023_2_QRC/en-US/56032dd760ca4790a55d069d4475b441.html "This document shows you how to use the monitoring views to monitor data lake Relational Engine system health, and to help you troubleshoot performance issues.") :arrow_upper_right: manual.

