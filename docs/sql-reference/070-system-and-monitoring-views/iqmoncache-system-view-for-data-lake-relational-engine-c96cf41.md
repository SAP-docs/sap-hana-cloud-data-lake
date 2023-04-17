<!-- loioc96cf41331eb48838d0ec95f79a637d6 -->

# iqmonCache System View for Data Lake Relational Engine

A server-level monitoring view providing cache size information for the IQ main store buffer cache, and IQ temporary store buffer cache. Cache sizes are shown as a share of overall server memory allocation.



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

CacheName



</td>
<td valign="top">

VARCHAR\(64\)



</td>
<td valign="top">

The name of the cache; either `Main Store Cache` or `Temp Store Cache`.



</td>
</tr>
<tr>
<td valign="top">

CacheSize



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The cache size, in MB. This value is also available in [sp\_iqstatus Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqstatus-procedure-for-data-lake-relational-engine-a5b8569.md) output.



</td>
</tr>
<tr>
<td valign="top">

NumberOfBuffers



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The number of buffers in the cache.



</td>
</tr>
<tr>
<td valign="top">

BuffersInUse



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The number of buffers in use in the cache.



</td>
</tr>
<tr>
<td valign="top">

NumberofPartitions



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The number of partitions in the cache.



</td>
</tr>
<tr>
<td valign="top">

PhysicalReads



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The number of pages read into the cache. This value is also available in [sp\_iqstatus Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqstatus-procedure-for-data-lake-relational-engine-a5b8569.md) output.



</td>
</tr>
<tr>
<td valign="top">

PhysicalWrites



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The number of buffers written from the cache. This value is also available in [sp\_iqstatus Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqstatus-procedure-for-data-lake-relational-engine-a5b8569.md) output.



</td>
</tr>
<tr>
<td valign="top">

TotalFinds



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The total number of searches of the cache. This value is also available in [sp\_iqstatus Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqstatus-procedure-for-data-lake-relational-engine-a5b8569.md) output.



</td>
</tr>
<tr>
<td valign="top">

TotalHits



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The total number of pages found in the cache. This value is also available in [sp\_iqstatus Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqstatus-procedure-for-data-lake-relational-engine-a5b8569.md) output.



</td>
</tr>
<tr>
<td valign="top">

TotalMisses



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The total number of searches that didn't find a page.



</td>
</tr>
<tr>
<td valign="top">

TotalBlocksRead



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The total number of blocks read into the cache.



</td>
</tr>
<tr>
<td valign="top">

TotalBlocksWritten



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The total number of blocks written from the cache.



</td>
</tr>
<tr>
<td valign="top">

TotalPrefetches



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The total number of pages read as prefetches.



</td>
</tr>
<tr>
<td valign="top">

TotalPrefetchMisses



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The total prefetch requests for pages that were not already available in the cache.



</td>
</tr>
<tr>
<td valign="top">

TotalPrefetchInMemory



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The total number of prefetch pages that were found in memory.



</td>
</tr>
<tr>
<td valign="top">

TotalGrabbedDirty



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The total number of buffers still waiting to be written when a clean buffer was needed.



</td>
</tr>
<tr>
<td valign="top">

TotalBusyWaits



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The total number of times buffer requests waited because a buffer was busy \(being read or modified\).



</td>
</tr>
</table>



<a name="loioc96cf41331eb48838d0ec95f79a637d6__section_kpt_vmz_1fb"/>

## Privileges

You must have the MONITOR system privilege to access this view. DBAs can consult [Granting a System Privilege to a User](https://help.sap.com/viewer/745778e524f74bb4af87460cca5e62c4/2023_1_QRC/en-US/a43bcb8284f210158039b1793a92a4fc.html "Allow the granting of specific system privileges to specific users, with or without administrative rights.") :arrow_upper_right: and [Alphabetical List of System Privileges for Data Lake Relational Engine](../080-sql-statements/alphabetical-list-of-system-privileges-for-data-lake-relational-engine-a449325.md) for information on granting the MONITOR system privilege to a user.



<a name="loioc96cf41331eb48838d0ec95f79a637d6__section_ahv_5mg_bfb"/>

## Use Cases

Use iqmonCache for diagnostic use-cases including:

-   Verifying that your IQ main cache and temporary cache sizes are correct by analyzing the cache hit ratio and physical reads metrics.

-   Evaluating prefetch manager efficiency by comparing the prefetch rate to the rate of physical reads.


iqmonCache, in conjunction with the other monitoring views, can help you troubleshoot common data lake Relational Engine performance problems. For diagnostic use-case information, see the [SAP HANA Cloud, Data Lake Performance and Tuning for Data Lake Relational Engine (Monitoring Views)](https://help.sap.com/viewer/028be133f34c4d2d998c6fbc258659c5/2023_1_QRC/en-US/56032dd760ca4790a55d069d4475b441.html "This document shows you how to use the monitoring views to monitor data lake Relational Engine system health, and to help you troubleshoot performance issues.") :arrow_upper_right: manual.

