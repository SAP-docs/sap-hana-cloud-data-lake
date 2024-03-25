<!-- loioa4da343584f210159719d7a4830c267f -->

# sp\_iqconnection Procedure for Data Lake Relational Engine

Shows information about connections and versions, including which users are using temporary dbspace, which users are keeping versions alive, what the connections are doing inside data lake Relational Engine, connection status, database version status, and so on.



<a name="loioa4da343584f210159719d7a4830c267f__section_vg4_vvh_b4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqconnection [ <connhandle> ]
```



<a name="loioa4da343584f210159719d7a4830c267f__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

*<connhandle\>*

</b></dt>
<dd>

The ID number of the connection.



</dd>
</dl>



<a name="loioa4da343584f210159719d7a4830c267f__IQ_Returns"/>

## Result Set


<table>
<tr>
<th valign="top">

Column Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

ConnHandle

</td>
<td valign="top">

The ID number of the connection

</td>
</tr>
<tr>
<td valign="top">

Name

</td>
<td valign="top">

The connection name specified by the ConnectionName \(CON\) connection parameter.

</td>
</tr>
<tr>
<td valign="top">

Userid

</td>
<td valign="top">

The user ID for the connection.

</td>
</tr>
<tr>
<td valign="top">

LastReqTime

</td>
<td valign="top">

The time at which the last request for the specified connection started.

</td>
</tr>
<tr>
<td valign="top">

ReqType

</td>
<td valign="top">

A string for the type of the last request.

</td>
</tr>
<tr>
<td valign="top">

IQCmdType

</td>
<td valign="top">

Data lake Relational Engine side, if any. The command type reflects commands defined at the implementation level of the engine. These commands consist of transaction commands, DDL and DML commands for data in the data lake Relational Engine store, internal data lake Relational Engine cursor commands, and special control commands such as the current command executing on the OPEN and CLOSE, and others.

</td>
</tr>
<tr>
<td valign="top">

LastIQCmdTime

</td>
<td valign="top">

The time the last data lake Relational Engine command started or completed on the IQ side of the data lake Relational Engine engine on this connection.

</td>
</tr>
<tr>
<td valign="top">

IQCursors

</td>
<td valign="top">

The number of cursors open in the data lake Relational Engine store on this connection.

</td>
</tr>
<tr>
<td valign="top">

LowestIQCursorState

</td>
<td valign="top">

The data lake Relational Engine cursor state, if any. If multiple cursors exist on the connection, the state that appears is the lowest cursor state of all the cursors; that is, the furthest from completion. Cursor state reflects internal data lake Relational Engine implementation detail and is subject to change in the future. Cursor states are:

-   NONE – no cursors have been rendered.
-   INITIALIZED – cursor is initialized.
-   PARSED – cursor is parsed and costed.
-   DESCRIBED – cursor information, such as column information, has been put into the descriptor.
-   COSTED – cursor cost has been costed.
-   PREPARED –statement has been prepared; cursor is executing.
-   EXECUTED – after PREPARED, cursor state transitions to EXECUTED.
-   FETCHING – fetching rows from cursor result set.
-   END\_OF\_DATA – seen the last record.
-   CLOSED – closed; DFO tree stays in place for reopen.
-   COMPLETED – is completed. Tearing down DFO tree.
-   INVALID – unrecoverable error occurred.

As suggested by the names, the cursor state changes at the end of the operation. A state of PREPARED, for example, indicates that the cursor is executing.

</td>
</tr>
<tr>
<td valign="top">

IQthreads

</td>
<td valign="top">

The number of data lake Relational Engine

</td>
</tr>
<tr>
<td valign="top">

TxnID

</td>
<td valign="top">

The transaction ID of the current transaction on the connection. This is the same as the transaction ID in the `.iqmsg` file by the BeginTxn, CmtTxn, and PostCmtTxn messages, as well as the Txn ID Seq logged when the database is opened.

</td>
</tr>
<tr>
<td valign="top">

ConnCreateTime

</td>
<td valign="top">

The time the connection was created.

</td>
</tr>
<tr>
<td valign="top">

TempTableSpaceKB

</td>
<td valign="top">

The number of kilobytes of data lake Relational Engine temporary store space in use by this connection for data stored in data lake Relational Engine temp tables. threads currently assigned to the connection. Some threads may be assigned but idle. This column can help you determine which connections are using the most resources. threads currently assigned to the connection. Some threads may be assigned but idle. This column can help you determine which connections are using the most resources.nullnullnull

</td>
</tr>
<tr>
<td valign="top">

TempWorkSpaceKB

</td>
<td valign="top">

nullThe number of kilobytes of data lake Relational Engine temporary store space in use by this connection for working space such as sorts, hashes, and temporary bitmaps. Space used by bitmaps or other objects that are part of indexes on data lake Relational Engine temporary tables are reflected in TempTableSpaceKB.

</td>
</tr>
<tr>
<td valign="top">

IQConnID

</td>
<td valign="top">

The 10-digit connection ID included as part of all messages in the `.iqmsg` file. This is a monotonically increasing integer unique within a server session.

</td>
</tr>
<tr>
<td valign="top">

satoiq\_count

</td>
<td valign="top">

An internal counter used to display the number of crossings from the SAP SQL Anywhere side to the data lake Relational Engine side of the data lake Relational Engine engine. This might be occasionally useful in determining connection activity. Result sets are returned in buffers of rows and don't increment satoiq\_count or iqtosa\_count once per row.

</td>
</tr>
<tr>
<td valign="top">

iqtosa\_count

</td>
<td valign="top">

An internal counter used to display the number of crossings from the data lake Relational Engine side to the SAP SQL Anywhere side of the data lake Relational Engine engine. This might be occasionally useful in determining connection activity.

</td>
</tr>
<tr>
<td valign="top">

CommLink

</td>
<td valign="top">

The communication link for the connection. This is one of the network protocols supported by data lake Relational Engine, or is local for a same-machine connection.

</td>
</tr>
<tr>
<td valign="top">

NodeAddr

</td>
<td valign="top">

The node for the client in a client/server connection.

</td>
</tr>
<tr>
<td valign="top">

LastIdle

</td>
<td valign="top">

The number of ticks between requests.

</td>
</tr>
<tr>
<td valign="top">

MPXServerName

</td>
<td valign="top">

If an INC connection, the VARCHAR\(128\) value contains the name of the node where the INC connection originates. NULL if not an INC connection.

</td>
</tr>
<tr>
<td valign="top">

INCConnName

</td>
<td valign="top">

The name of the underlying INC connection for a user connection. The data type for this column is VARCHAR\(255\). If sp\_iqconnection shows an INC connection name for a suspended user connection that user connection has an associated INC connection that is also suspended.

</td>
</tr>
<tr>
<td valign="top">

INCConnSuspended

</td>
<td valign="top">

The value "Y" in this column indicates that the underlying INC connection for a user connection is in a suspended state. The value "N" indicates that the connection isn't suspended.

</td>
</tr>
</table>



<a name="loioa4da343584f210159719d7a4830c267f__IQ_Remarks"/>

## Remarks

*<connhandle\>* is equal to the Number connection property and is the ID number of the connection. The connection\_property system function returns the connection ID:

```
SELECT connection_property ( 'Number' )
```

When called with an input parameter of a valid *<connhandle\>*, sp\_iqconnection returns the one row for that connection only.

sp\_iqconnection returns a row for each active connection. The columns ConnHandle, Name, Userid, LastReqTime, ReqType, CommLink, NodeAddr, and LastIdle are the connection properties Number, Name, Userid, LastReqTime, ReqType, CommLink, NodeAddr, and LastIdle, respectively, and return the same values as the system function sa\_conn\_info. The additional columns return connection data from the data lake Relational Engine side of the data lake Relational Engine engine. Rows are ordered by ConnCreateTime.

The column MPXServerName stores information related to internode communication \(INC\), as shown:


<table>
<tr>
<th valign="top">

Server Where Run

</th>
<th valign="top">

MPXServerName Column Content

</th>
</tr>
<tr>
<td valign="top">

Data lake Relational Engine server

</td>
<td valign="top">

NULL \(All connections are local/user connections\)

</td>
</tr>
<tr>
<td valign="top">

Coordinator node

</td>
<td valign="top">

-   NULL for local or user connections.
-   Contains value of worker node's name \(source of connection\) for every INC connection \(either on-demand or dedicated heartbeat connection\).



</td>
</tr>
<tr>
<td valign="top">

Worker node

</td>
<td valign="top">

-   NULL for local or user connections.
-   Contains value of coordinator's name \(source of connection\).



</td>
</tr>
</table>

In Java applications, specify data lake Relational Engine-specific connection properties from TDS clients in the RemotePWD field. This example, where myconnection becomes the data lake Relational Engine connection name, shows how to specify data lake Relational Engine-specific connection parameters:

```
p.put("RemotePWD",",,CON=myconnection");
```



<a name="loioa4da343584f210159719d7a4830c267f__IQ_Privileges"/>

## Privileges

Requires all of:

-   EXECUTE object-level privilege on the procedure
-   MONITOR system privilege



<a name="loioa4da343584f210159719d7a4830c267f__IQ_Side_Effects"/>

## Side Effects

None



<a name="loioa4da343584f210159719d7a4830c267f__section_dnh_dyx_tzb"/>

## Examples

This example returns information on connection 602508:

```
CALL sp_iqconnection (602508);
```


<table>
<tr>
<th valign="top">

ConnHandle

</th>
<th valign="top">

Name

</th>
<th valign="top">

Userid

</th>
<th valign="top">

LastReqTime

</th>
<th valign="top">

ReqType

</th>
<th valign="top">

IQCmdType

</th>
<th valign="top">

LastIQCmdTime

</th>
<th valign="top">

IQCursors

</th>
</tr>
<tr>
<td valign="top">

602508

</td>
<td valign="top">

 

</td>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

19:20.8

</td>
<td valign="top">

OPEN

</td>
<td valign="top">

IQUTILITYOPENCURSOR

</td>
<td valign="top">

19:20.8

</td>
<td valign="top">

0

</td>
</tr>
</table>


<table>
<tr>
<th valign="top" colspan="7">

\(Continued\)

</th>
</tr>
<tr>
<th valign="top">

LowestIQCursorState

</th>
<th valign="top">

IQthreads

</th>
<th valign="top">

TxnID

</th>
<th valign="top">

ConnCreateTime

</th>
<th valign="top">

TempTableSpaceKB

</th>
<th valign="top">

TempWorkSpaceKB

</th>
<th valign="top">

IQconnID

</th>
</tr>
<tr>
<td valign="top">

NONE

</td>
<td valign="top">

0

</td>
<td valign="top">

16576516

</td>
<td valign="top">

13:45.4

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

912637

</td>
</tr>
</table>


<table>
<tr>
<th valign="top" colspan="9">

\(Continued\)

</th>
</tr>
<tr>
<th valign="top">

satoiq\_count

</th>
<th valign="top">

iqtosa\_count

</th>
<th valign="top">

CommLink

</th>
<th valign="top">

NodeAddr

</th>
<th valign="top">

LastIdle

</th>
<th valign="top">

MPXServerName

</th>
<th valign="top">

LSName

</th>
<th valign="top">

INCConnName

</th>
<th valign="top">

INCConnSuspended

</th>
</tr>
<tr>
<td valign="top">

46

</td>
<td valign="top">

2

</td>
<td valign="top">

TCPIP

</td>
<td valign="top">

52.57.33.140

</td>
<td valign="top">

7886

</td>
<td valign="top">

 

</td>
<td valign="top">

OPEN

</td>
<td valign="top">

 

</td>
<td valign="top">

N

</td>
</tr>
</table>

