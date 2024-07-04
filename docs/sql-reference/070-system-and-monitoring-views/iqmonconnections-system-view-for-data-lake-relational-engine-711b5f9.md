<!-- loio711b5f9ca171400ca7efa6a48e559a78 -->

# iqmonConnections System View for Data Lake Relational Engine

A server-level monitoring view providing current connection status information such as connection ID and connection creation time, as well as last request time and temp table space utilization.



<a name="loio711b5f9ca171400ca7efa6a48e559a78__section_skb_fwg_k4b"/>

## Usage

This data lake Relational Engine system view can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



> ### Tip:  
> All columns in this view are also available in [sp\_iqconnection System Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqconnection-system-procedure-for-data-lake-relational-engine-a4da343.md) output.


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

ConnectionHandle

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

The connection handle for this connection.

</td>
</tr>
<tr>
<td valign="top">

ConnectionName

</td>
<td valign="top">

VARCHAR\(255\)

</td>
<td valign="top">

The name of the connection. This is an internal name.

</td>
</tr>
<tr>
<td valign="top">

UserID

</td>
<td valign="top">

VARCHAR\(255\)

</td>
<td valign="top">

The user ID.

</td>
</tr>
<tr>
<td valign="top">

LastRequestTime

</td>
<td valign="top">

VARCHAR\(255\)

</td>
<td valign="top">

The time of the last request by this connection.

</td>
</tr>
<tr>
<td valign="top">

LastRequestType

</td>
<td valign="top">

VARCHAR\(255\)

</td>
<td valign="top">

The last request type.

</td>
</tr>
<tr>
<td valign="top">

IQCommandType

</td>
<td valign="top">

CHAR\(32\)

</td>
<td valign="top">

The type of command.

</td>
</tr>
<tr>
<td valign="top">

LastIQCommandTime

</td>
<td valign="top">

DATETIME\(8\)

</td>
<td valign="top">

The time of the last data lake Relational Engine command executed by this connection.

</td>
</tr>
<tr>
<td valign="top">

IQCursors

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

The number of data lake Relational Engine cursors for this connection.

</td>
</tr>
<tr>
<td valign="top">

LowestIQCursorState

</td>
<td valign="top">

CHAR\(16\)

</td>
<td valign="top">

The lowest data lake Relational Engine cursor state.

</td>
</tr>
<tr>
<td valign="top">

IQThreads

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

The number of data lake Relational Engine threads in use by this connection.

</td>
</tr>
<tr>
<td valign="top">

TransactionID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

The current transaction ID for this connection.

</td>
</tr>
<tr>
<td valign="top">

ConnectionCreateTime

</td>
<td valign="top">

DATETIME\(8\)

</td>
<td valign="top">

The creation time for this connection.

</td>
</tr>
<tr>
<td valign="top">

TempTableSpace

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

The temporary table space \(in KB\) used by this connection.

</td>
</tr>
<tr>
<td valign="top">

TempWorkSpace

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

The temporary work space \(in KB\) used by this connection.

</td>
</tr>
<tr>
<td valign="top">

IQConnectionID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

The data lake Relational Engine connection ID.

</td>
</tr>
<tr>
<td valign="top">

SAtoIQCalls

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

The number of interface calls from SAP SQL Anywhere to data lake Relational Engine.

</td>
</tr>
<tr>
<td valign="top">

IQtoSACalls

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

The number of interface calls from data lake Relational Engine to SAP SQL Anywhere.

</td>
</tr>
<tr>
<td valign="top">

CommunicationLink

</td>
<td valign="top">

VARCHAR\(255\)

</td>
<td valign="top">

The communication link for this connection.

</td>
</tr>
<tr>
<td valign="top">

NodeAddress

</td>
<td valign="top">

VARCHAR\(255\)

</td>
<td valign="top">

The multiplex node that this connection is connected to.

</td>
</tr>
<tr>
<td valign="top">

LastIdlePeriod

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

The number of clock ticks between requests.

</td>
</tr>
<tr>
<td valign="top">

MPXServerName

</td>
<td valign="top">

VARCHAR\(255\)

</td>
<td valign="top">

The name of the originating server if this is an internode communication connection.

</td>
</tr>
<tr>
<td valign="top">

INCConnectionName

</td>
<td valign="top">

VARCHAR\(255\)

</td>
<td valign="top">

The name of the underlying internode communication connection for this connection.

</td>
</tr>
<tr>
<td valign="top">

INCConnectionSuspended

</td>
<td valign="top">

CHAR\(2\)

</td>
<td valign="top">

Indicates whether the internode communication connection is suspended \('Y' or 'N'\).

</td>
</tr>
</table>



<a name="loio711b5f9ca171400ca7efa6a48e559a78__section_kpt_vmz_1fb"/>

## Privileges

You must have the MONITOR system privilege to access this view. DBAs can consult [Granting and Revoking a System Privilege from Users and Roles](https://help.sap.com/viewer/a89a0a8384f21015b1e7adbeca456f73/2024_3_QRC/en-US/a43bcb8284f210158039b1793a92a4fc.html "Grant and revoke a specific system privilege to and from specific users or roles, with or without administrative rights.") :arrow_upper_right: and [Alphabetical List of System Privileges for Data Lake Relational Engine](../080-sql-statements/alphabetical-list-of-system-privileges-for-data-lake-relational-engine-a449325.md) for information on granting the MONITOR system privilege to a user.



<a name="loio711b5f9ca171400ca7efa6a48e559a78__section_ahv_5mg_bfb"/>

## Use Cases

Use iqmonConnections for diagnostic use-cases including:

-   Showing server load by listing the current active connections.

-   Determining the address of the host for a connection

-   Determining how much temporary cache is consumed by a connection.


iqmonConnections, in conjunction with the other monitoring views, can help you troubleshoot common data lake Relational Engine performance problems. For diagnostic use-case information, see the [SAP HANA Cloud, Data Lake Performance and Tuning for Data Lake Relational Engine (Monitoring Views)](https://help.sap.com/viewer/028be133f34c4d2d998c6fbc258659c5/2024_3_QRC/en-US/56032dd760ca4790a55d069d4475b441.html "This document shows you how to use the monitoring views to monitor data lake Relational Engine system health, and to help you troubleshoot performance issues.") :arrow_upper_right: manual.

