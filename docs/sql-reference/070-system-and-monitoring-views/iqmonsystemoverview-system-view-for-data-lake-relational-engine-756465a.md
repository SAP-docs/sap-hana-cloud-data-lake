<!-- loio756465a668ad4a1ba91f6c0b46b18e53 -->

# iqmonSystemOverview System View for Data Lake Relational Engine

A server-level monitoring view for troubleshooting performance issues. iqmonSystemOverview provides high-level system overview information including total memory, CPU utilization, number of threads, number of connections, product version, and metrics for main cache and temporary cache usage.



<a name="loio756465a668ad4a1ba91f6c0b46b18e53__section_skb_fwg_k4b"/>

## Usage

This data lake Relational Engine system view can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.


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

SystemName

</td>
<td valign="top">

VARCHAR\(50\)

</td>
<td valign="top">

The data lake Relational Engine server name.

</td>
</tr>
<tr>
<td valign="top">

DatabaseName

</td>
<td valign="top">

VARCHAR\(128\)

</td>
<td valign="top">

The data lake Relational Engine database name.

</td>
</tr>
<tr>
<td valign="top">

HostName

</td>
<td valign="top">

VARCHAR\(64\)

</td>
<td valign="top">

The name of the data lake Relational Engine host machine.

</td>
</tr>
<tr>
<td valign="top">

IQServerVersion

</td>
<td valign="top">

VARCHAR\(128\)

</td>
<td valign="top">

The version number of the installed data lake Relational Engine support package or patch release. This value is also available in [sp\_iqstatus Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqstatus-procedure-for-data-lake-relational-engine-a5b8569.md) output.

</td>
</tr>
<tr>
<td valign="top">

ActiveConnections

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The current number of connections to the data lake Relational Engine server. This value is also available in [sp\_iqstatistics Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqstatistics-procedure-for-data-lake-relational-engine-a5b7d32.md) output.

</td>
</tr>
<tr>
<td valign="top">

ActiveTransactions

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The current number of active transactions.

</td>
</tr>
<tr>
<td valign="top">

NumberOfActiveVersions

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The current number of active versions.

</td>
</tr>
<tr>
<td valign="top">

ServerMode

</td>
<td valign="top">

VARCHAR\(64\)

</td>
<td valign="top">

The data lake Relational Engine server mode: either `IQ Server`, `IQ Multiplex Coordinator Server`, `IQ Multiplex Write Server`, or `IQ Multiplex Query Server`. This value is also available in [sp\_iqstatus Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqstatus-procedure-for-data-lake-relational-engine-a5b8569.md) output.

</td>
</tr>
<tr>
<td valign="top">

PageSize

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The data lake Relational Engine database page size, in KB. This value is also available in [sp\_iqstatus Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqstatus-procedure-for-data-lake-relational-engine-a5b8569.md) output.

</td>
</tr>
<tr>
<td valign="top">

HeapMemory

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The data lake Relational Engine server heap memory size, in MB. This value is also available in [sp\_iqstatus Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqstatus-procedure-for-data-lake-relational-engine-a5b8569.md) output.

</td>
</tr>
<tr>
<td valign="top">

DynamicMemory

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The data lake Relational Engine dynamic memory size, in MB. This value is also available in [sp\_iqstatus Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqstatus-procedure-for-data-lake-relational-engine-a5b8569.md) output.

</td>
</tr>
<tr>
<td valign="top">

LastFullBackupTime

</td>
<td valign="top">

DATETIME

</td>
<td valign="top">

The time of the last full data lake Relational Engine database backup. This value is also available in [sp\_iqstatus Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqstatus-procedure-for-data-lake-relational-engine-a5b8569.md) output.

</td>
</tr>
<tr>
<td valign="top">

LastBackupTime

</td>
<td valign="top">

DATETIME

</td>
<td valign="top">

The time of the last data lake Relational Engine database backup.

</td>
</tr>
<tr>
<td valign="top">

StartTime

</td>
<td valign="top">

DATETIME

</td>
<td valign="top">

The start time of the data lake Relational Engine server.

</td>
</tr>
<tr>
<td valign="top">

UserCPUTime

</td>
<td valign="top">

FLOAT

</td>
<td valign="top">

The amount of system mode CPU time used by the data lake Relational Engine server, in seconds. This value is also available in [sp\_iqstatistics Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqstatistics-procedure-for-data-lake-relational-engine-a5b7d32.md) output.

</td>
</tr>
<tr>
<td valign="top">

SystemCPUTime

</td>
<td valign="top">

FLOAT

</td>
<td valign="top">

The total CPU time used by the data lake Relational Engine server in seconds. This value is also available in [sp\_iqstatistics Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqstatistics-procedure-for-data-lake-relational-engine-a5b7d32.md) output.

</td>
</tr>
<tr>
<td valign="top">

TotalCPUTime

</td>
<td valign="top">

FLOAT

</td>
<td valign="top">

The amount of user mode CPU time used by the data lake Relational Engine server, in seconds. This value is also available in [sp\_iqstatistics Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqstatistics-procedure-for-data-lake-relational-engine-a5b7d32.md) output.

</td>
</tr>
<tr>
<td valign="top">

MainFinds

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

The number of finds of the main cache. This value is also available in [sp\_iqstatistics Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqstatistics-procedure-for-data-lake-relational-engine-a5b7d32.md) output.

</td>
</tr>
<tr>
<td valign="top">

MainHitRatio

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

The ratio of buffers found in the main cache to the total number of finds. This value is also available in [sp\_iqstatistics Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqstatistics-procedure-for-data-lake-relational-engine-a5b7d32.md) output.

</td>
</tr>
<tr>
<td valign="top">

MainReads

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

The number of read operations for the main cache. This value is also available in [sp\_iqstatistics Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqstatistics-procedure-for-data-lake-relational-engine-a5b7d32.md) output.

</td>
</tr>
<tr>
<td valign="top">

MainWrites

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

The number of pages written from the main cache. This value is also available in [sp\_iqstatistics Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqstatistics-procedure-for-data-lake-relational-engine-a5b7d32.md) output.

</td>
</tr>
<tr>
<td valign="top">

TempFinds

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

The number of finds of the temporary cache. This value is also available in [sp\_iqstatistics Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqstatistics-procedure-for-data-lake-relational-engine-a5b7d32.md) output.

</td>
</tr>
<tr>
<td valign="top">

TempHitRatio

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

The ratio of buffers found in the temp cache to the total number of finds.

</td>
</tr>
<tr>
<td valign="top">

TempReads

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

The number of read operations for the temporary cache. This value is also available in [sp\_iqstatistics Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqstatistics-procedure-for-data-lake-relational-engine-a5b7d32.md) output.

</td>
</tr>
<tr>
<td valign="top">

TempWrites

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

The number of pages written from the temporary cache. This value is also available in [sp\_iqstatistics Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqstatistics-procedure-for-data-lake-relational-engine-a5b7d32.md) output.

</td>
</tr>
</table>



<a name="loio756465a668ad4a1ba91f6c0b46b18e53__section_kpt_vmz_1fb"/>

## Privileges

You must have the MONITOR system privilege to access this view. DBAs can consult [Granting a System Privilege to a User](https://help.sap.com/viewer/745778e524f74bb4af87460cca5e62c4/2023_4_QRC/en-US/a43bcb8284f210158039b1793a92a4fc.html "Allow the granting of specific system privileges to specific users, with or without administrative rights.") :arrow_upper_right: and [Alphabetical List of System Privileges for Data Lake Relational Engine](../080-sql-statements/alphabetical-list-of-system-privileges-for-data-lake-relational-engine-a449325.md) for information on granting the MONITOR system privilege to a user.



<a name="loio756465a668ad4a1ba91f6c0b46b18e53__section_ahv_5mg_bfb"/>

## Use Cases

Use iqmonSystemOverview for diagnostic use-cases including:

-   Reporting key data lake Relational Engine server information such as software version, platform, and host name.

-   Determining the current server memory allocation.

-   Determining the date and time of the last database backups.

-   Verifying if CPU utilization is outside of the normal range.


iqmonSystemOverview, in conjunction with the other monitoring views, can help you troubleshoot common data lake Relational Engine performance problems. For diagnostic use-case information, see the [SAP HANA Cloud, Data Lake Performance and Tuning for Data Lake Relational Engine (Monitoring Views)](https://help.sap.com/viewer/028be133f34c4d2d998c6fbc258659c5/2023_4_QRC/en-US/56032dd760ca4790a55d069d4475b441.html "This document shows you how to use the monitoring views to monitor data lake Relational Engine system health, and to help you troubleshoot performance issues.") :arrow_upper_right: manual.

