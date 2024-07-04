<!-- loiod269c4f0f1bb4e90a46fc02ed017c4ad -->

# iqmonLocks System View for Data Lake Relational Engine

A server-level monitoring view providing information about locks in the database, including the user or connection holding a lock, and how long the lock has been open.



<a name="loiod269c4f0f1bb4e90a46fc02ed017c4ad__section_skb_fwg_k4b"/>

## Usage

This data lake Relational Engine system view can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



> ### Note:  
> All columns in this view are also available in [sp\_iqlocks System Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqlocks-system-procedure-for-data-lake-relational-engine-a5af357.md) output.


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

ConnectionName

</td>
<td valign="top">

VARCHAR\(128\)

</td>
<td valign="top">

The name of the connection holding the lock.

</td>
</tr>
<tr>
<td valign="top">

ConnectionID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

The connection ID for the connection holding the lock.

</td>
</tr>
<tr>
<td valign="top">

UserID

</td>
<td valign="top">

VARCHAR\(128\)

</td>
<td valign="top">

The user ID for the connection holding the lock.

</td>
</tr>
<tr>
<td valign="top">

TableType

</td>
<td valign="top">

CHAR\(6\)

</td>
<td valign="top">

The type of table.

</td>
</tr>
<tr>
<td valign="top">

TableCreator

</td>
<td valign="top">

VARCHAR\(128\)

</td>
<td valign="top">

The owner of the table.

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

The name of the table on which the lock is held.

</td>
</tr>
<tr>
<td valign="top">

IndexID

</td>
<td valign="top">

INTEGER\(4\)

</td>
<td valign="top">

The index ID, or null.

</td>
</tr>
<tr>
<td valign="top">

LockClass

</td>
<td valign="top">

CHAR\(8\)

</td>
<td valign="top">

The lock class \(schema, table, row, or position\).

</td>
</tr>
<tr>
<td valign="top">

LockDuration

</td>
<td valign="top">

CHAR\(11\)

</td>
<td valign="top">

The duration of the lock \(transaction, position, or connection\).

</td>
</tr>
<tr>
<td valign="top">

LockType

</td>
<td valign="top">

CHAR\(9\)

</td>
<td valign="top">

The lock type.

</td>
</tr>
<tr>
<td valign="top">

RowID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

The starting row ID for row locks.

</td>
</tr>
<tr>
<td valign="top">

RowRange

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

The number of contiguous rows that are locked.

</td>
</tr>
</table>



<a name="loiod269c4f0f1bb4e90a46fc02ed017c4ad__section_kpt_vmz_1fb"/>

## Privileges

You must have the MONITOR system privilege to access this view. DBAs can consult [Granting and Revoking a System Privilege from Users and Roles](https://help.sap.com/viewer/a89a0a8384f21015b1e7adbeca456f73/2024_3_QRC/en-US/a43bcb8284f210158039b1793a92a4fc.html "Grant and revoke a specific system privilege to and from specific users or roles, with or without administrative rights.") :arrow_upper_right: and [Alphabetical List of System Privileges for Data Lake Relational Engine](../080-sql-statements/alphabetical-list-of-system-privileges-for-data-lake-relational-engine-a449325.md) for information on granting the MONITOR system privilege to a user.



<a name="loiod269c4f0f1bb4e90a46fc02ed017c4ad__section_ahv_5mg_bfb"/>

## Use Cases

Use iqmonLocks for diagnostic use-cases including:

-   Identifying the user or connection holding important locks, such as table locks or forbid locks.

-   Identifying those locks that have been open for an excessive length of time.


iqmonLocks, in conjunction with the other monitoring views, can help you troubleshoot common data lake Relational Engine performance problems. For diagnostic use-case information, see the [SAP HANA Cloud, Data Lake Performance and Tuning for Data Lake Relational Engine (Monitoring Views)](https://help.sap.com/viewer/028be133f34c4d2d998c6fbc258659c5/2024_3_QRC/en-US/56032dd760ca4790a55d069d4475b441.html "This document shows you how to use the monitoring views to monitor data lake Relational Engine system health, and to help you troubleshoot performance issues.") :arrow_upper_right: manual.

