<!-- loiof182cdc23a104bda842a61fd7c0e8967 -->

# iqmonCacheDetails System View for Data Lake Relational Engine

A server-level monitoring view providing details of both the IQ main cache and temporary cache. Details include object names, object cache space utilization, and page type.



<a name="loiof182cdc23a104bda842a61fd7c0e8967__section_skb_fwg_k4b"/>

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

CacheName

</td>
<td valign="top">

VARCHAR\(128\)

</td>
<td valign="top">

The name of the cache.

</td>
</tr>
<tr>
<td valign="top">

ObjectName

</td>
<td valign="top">

VARCHAR\(128\)

</td>
<td valign="top">

The name of the object being reported on.

</td>
</tr>
<tr>
<td valign="top">

ObjectOwner

</td>
<td valign="top">

VARCHAR\(128\)

</td>
<td valign="top">

The name of the object's owner.

</td>
</tr>
<tr>
<td valign="top">

TableName

</td>
<td valign="top">

VARCHAR\(128\)

</td>
<td valign="top">

The name of the table.

</td>
</tr>
<tr>
<td valign="top">

ObjectType

</td>
<td valign="top">

VARCHAR\(128\)

</td>
<td valign="top">

The type of object.

</td>
</tr>
<tr>
<td valign="top">

NumberOfBuffers

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

The number of buffers for the object holding the page type.

</td>
</tr>
<tr>
<td valign="top">

CachedSize

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

The total size of all the buffers occupied by the object.

</td>
</tr>
<tr>
<td valign="top">

UniqueID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

The unique ID of the blockmap for the object.

</td>
</tr>
<tr>
<td valign="top">

NumberOfVersions

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

The number of versions.

</td>
</tr>
</table>



<a name="loiof182cdc23a104bda842a61fd7c0e8967__section_kpt_vmz_1fb"/>

## Privileges

You must have the MONITOR system privilege to access this view. DBAs can consult [Granting and Revoking a System Privilege from Users and Roles](https://help.sap.com/viewer/a89a0a8384f21015b1e7adbeca456f73/2024_3_QRC/en-US/a43bcb8284f210158039b1793a92a4fc.html "Grant and revoke a specific system privilege to and from specific users or roles, with or without administrative rights.") :arrow_upper_right: and [Alphabetical List of System Privileges for Data Lake Relational Engine](../080-sql-statements/alphabetical-list-of-system-privileges-for-data-lake-relational-engine-a449325.md) for information on granting the MONITOR system privilege to a user.



<a name="loiof182cdc23a104bda842a61fd7c0e8967__section_ahv_5mg_bfb"/>

## Use Cases

Use iqmonCacheDetails for diagnostic use-cases including:

-   Verifying if queries are consuming more cache than expected.

-   Identifying the users or connections consuming the greatest amount of temporary cache.

-   Determining if your IQ main cache and temporary cache sizes are sufficient.


iqmonCacheDetails, in conjunction with the other monitoring views, can help you troubleshoot common data lake Relational Engine performance problems. For diagnostic use-case information, see the [SAP HANA Cloud, Data Lake Performance and Tuning for Data Lake Relational Engine (Monitoring Views)](https://help.sap.com/viewer/028be133f34c4d2d998c6fbc258659c5/2024_3_QRC/en-US/56032dd760ca4790a55d069d4475b441.html "This document shows you how to use the monitoring views to monitor data lake Relational Engine system health, and to help you troubleshoot performance issues.") :arrow_upper_right: manual.

