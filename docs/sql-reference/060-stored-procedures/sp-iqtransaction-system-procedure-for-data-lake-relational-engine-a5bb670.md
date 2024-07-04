<!-- loioa5bb670c84f21015b392b24dcf28be14 -->

# sp\_iqtransaction System Procedure for Data Lake Relational Engine

Shows information about transactions and versions.



<a name="loioa5bb670c84f21015b392b24dcf28be14__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqtransaction
```



<a name="loioa5bb670c84f21015b392b24dcf28be14__section_ddw_xrm_nbb"/>

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

Name

</td>
<td valign="top">

The name of the application.

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

TxnID

</td>
<td valign="top">

The transaction ID of this transaction control block. The transaction ID is assigned during `begin transaction`. It appears in the `.iqmsg` file by the BeginTxn, CmtTxn, and PostCmtTxn messages, and is the same as the Txn ID Seq that is logged when the database is opened.

</td>
</tr>
<tr>
<td valign="top">

CmtID

</td>
<td valign="top">

The ID assigned by the transaction manager when the transaction commits. For active transactions, the CmtID is zero.

</td>
</tr>
<tr>
<td valign="top">

VersionID

</td>
<td valign="top">

A value of 0 indicates that the transaction is unversioned, and the VersionID hasn't been assigned.

For the coordinator node, the VersionID is assigned after the transaction establishes table locks. Worker nodes receive the VersionID from the coordinator. The VersionID is used internally by the data lake Relational Engine in-memory catalog and the IQ transaction manager to uniquely identify a database version to all nodes.

</td>
</tr>
<tr>
<td valign="top">

State

</td>
<td valign="top">

The state of the transaction control block. This variable reflects internal data lake Relational Engine implementation details and is subject to change in the future. Currently, transaction states are NONE, ACTIVE, ROLLING\_BACK, ROLLED\_BACK, COMMITTING, COMMITTED, and APPLIED.

NONE, ROLLING\_BACK, ROLLED\_BACK, COMMITTING and APPLIED are transient states with a very small life span.

ACTIVE indicates that the transaction is active.

COMMITTED indicates that the transaction has completed and is waiting to be APPLIED, at which point a version that is invisible to any transaction is subject to garbage collection.

Once the transaction state is ROLLED\_BACK, COMMITTED, or APPLIED, ceases to own any locks other than those held by open cursors.

</td>
</tr>
<tr>
<td valign="top">

ConnHandle

</td>
<td valign="top">

The ID number of the connection.

</td>
</tr>
<tr>
<td valign="top">

IQConnID

</td>
<td valign="top">

The 10-digit connection ID that is included as part of all messages in the `.iqmsg` file. This is a monotonically increasing integer unique within a server session.

</td>
</tr>
<tr>
<td valign="top">

MainTableKBCr

</td>
<td valign="top">

The number of kilobytes of data lake Relational Engine store space created by this transaction.

</td>
</tr>
<tr>
<td valign="top">

MainTableKBDr

</td>
<td valign="top">

The number of kilobytes of data lake Relational Engine store space dropped by this transaction, but that persist on disk in the store because the space is visible in other database versions or other savepoints of this transaction.

</td>
</tr>
<tr>
<td valign="top">

TempTableKBCr

</td>
<td valign="top">

The number of kilobytes of data lake Relational Engine temporary store space created by this transaction for storage of data lake Relational Engine temporary table data.

</td>
</tr>
<tr>
<td valign="top">

TempTableKBDr

</td>
<td valign="top">

The number of kilobytes of data lake Relational Engine temporary table space dropped by this transaction, but which persist on disk in the data lake Relational Engine temporary store because the space is visible to data lake Relational Engine cursors or is owned by other savepoints of this transaction.

</td>
</tr>
<tr>
<td valign="top">

TempWorkSpaceKB

</td>
<td valign="top">

For ACTIVE transactions, a snapshot of the work space in use at this instant by this transaction, such as sorts, hashes, and temporary bitmaps. The number varies depending on when you run sp\_iqtransaction. For example, the query engine might create 60 MB in the temporary cache but release most of it quickly, even though query processing continues. If you run sp\_iqtransaction after the query finishes, this column shows a much smaller number. When the transaction is no longer active, this column is zero.

For ACTIVE transactions, this column is the same as the TempWorkSpaceKB column of sp\_iqconnection.

</td>
</tr>
<tr>
<td valign="top">

TxnCreateTime

</td>
<td valign="top">

The time the transaction began. All data lake Relational Engine transactions begin implicitly as soon as an active connection is established or when the previous transaction commits or rolls back.

</td>
</tr>
<tr>
<td valign="top">

CursorCount

</td>
<td valign="top">

The number of open data lake Relational Engine cursors that reference this transaction control block. If the transaction is ACTIVE, it indicates the number of open cursors created within the transaction. If the transaction is COMMITTED, it indicates the number of hold cursors that reference a database version owned by this transaction control block.

</td>
</tr>
<tr>
<td valign="top">

SpCount

</td>
<td valign="top">

The number of savepoint structures that exist within the transaction control block. Savepoints may be created and released implicitly. Therefore, this number doesn't indicate the number of user-created savepoints within the transaction.

</td>
</tr>
<tr>
<td valign="top">

SpNumber

</td>
<td valign="top">

The active savepoint number of the transaction. This is an implementation detail and might not reflect a user-created savepoint.

</td>
</tr>
<tr>
<td valign="top">

MPXServerName

</td>
<td valign="top">

Indicates if an active transaction is from an internode communication \(INC\) connection. If from INC connection, the value is the name of the node where the transaction originates. NULL if not from an INC connection. Always NULL if the transaction isn't active.

</td>
</tr>
<tr>
<td valign="top">

GlobalTxnID

</td>
<td valign="top">

The global transaction ID associated with the current transaction, 0 \(zero\) if none.

</td>
</tr>
<tr>
<td valign="top">

VersioningType

</td>
<td valign="top">

The snapshot versioning type of the transaction; table-level is the default.

</td>
</tr>
<tr>
<td valign="top">

Blocking

</td>
<td valign="top">

Indicates if connection blocking is enabled \(True\) or disabled \(False\). You set connection blocking using the `BLOCKING` database option. If true, the transaction blocks, meaning it waits for a conflicting lock to release before it attempts to retry the lock request.

</td>
</tr>
<tr>
<td valign="top">

BlockingTimeout

</td>
<td valign="top">

Indicates the time, in milliseconds, a transaction waits for a locking conflict to clear. You set the timeout threshold using the `BLOCKING_TIMEOUT` database option. A value of 0 \(default\) indicates that the transaction waits indefinitely.

</td>
</tr>
</table>



<a name="loioa5bb670c84f21015b392b24dcf28be14__iq_refbb_1817"/>

## Remarks

sp\_iqtransaction returns a row for each transaction control block in the data lake Relational Engine transaction manager. The columns Name, Userid, and ConnHandle are the connection properties Name, Userid, and Number, respectively. Rows are ordered by TxnID.

sp\_iqtransaction output doesn't include connections without transactions in progress. To include all connections, use sp\_iqconnection.

> ### Note:  
> Although you can use sp\_iqtransaction to identify users who are blocking other users from writing to a table, sp\_iqlocks is a better choice for this purpose.



<a name="loioa5bb670c84f21015b392b24dcf28be14__iq_refbb_1816"/>

## Privileges

Requires all of the following:

-   EXECUTE object-level privilege on this procedure
-   MONITOR system privilege



## Side Effects

None.



<a name="loioa5bb670c84f21015b392b24dcf28be14__iq_refbb_1819"/>

## Examples

This example returns information about transactions and versions.

```
CALL sp_iqtransaction;
```


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Userid

</th>
<th valign="top">

TxnID

</th>
<th valign="top">

CmtID

</th>
<th valign="top">

VersionID

</th>
<th valign="top">

State

</th>
<th valign="top">

Conn

Handle

</th>
<th valign="top">

IQ

ConnID

</th>
<th valign="top">

Main

Table

KBCr

</th>
<th valign="top">

Main

Table

KBDr

</th>
<th valign="top">

Temp

Table

KBCr

</th>
</tr>
<tr>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

446204

</td>
<td valign="top">

446205

</td>
<td valign="top">

206829

</td>
<td valign="top">

APPLIED

</td>
<td valign="top">

1000240026

</td>
<td valign="top">

299433

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

446245

</td>
<td valign="top">

446246

</td>
<td valign="top">

206851

</td>
<td valign="top">

APPLIED

</td>
<td valign="top">

1000240039

</td>
<td valign="top">

299455

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

446345

</td>
<td valign="top">

446346

</td>
<td valign="top">

206855

</td>
<td valign="top">

APPLIED

</td>
<td valign="top">

1000240054

</td>
<td valign="top">

299482

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

446378

</td>
<td valign="top">

0

</td>
<td valign="top">

206855

</td>
<td valign="top">

ACTIVE

</td>
<td valign="top">

328895

</td>
<td valign="top">

299495

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

446927

</td>
<td valign="top">

446928

</td>
<td valign="top">

206941

</td>
<td valign="top">

COMMITTED

</td>
<td valign="top">

1000240222

</td>
<td valign="top">

299734

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
</tr>
</table>


<table>
<tr>
<th valign="top" colspan="11">

\(Continued\)

</th>
</tr>
<tr>
<th valign="top">

Temp

Table

KBDr

</th>
<th valign="top">

TempWork

SpaceKB

</th>
<th valign="top">

TxnCreate

Time

</th>
<th valign="top">

Cursor

Count

</th>
<th valign="top">

SpCount

</th>
<th valign="top">

SpNumber

</th>
<th valign="top">

MPXServer

Name

</th>
<th valign="top">

Global

TxnID

</th>
<th valign="top">

Versioning

Type

</th>
<th valign="top">

Blocking

</th>
<th valign="top">

Blocking

Timeout

</th>
</tr>
<tr>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

2024-06-20 17:13:04.440

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

NULL

</td>
<td valign="top">

0

</td>
<td valign="top">

Table-level

</td>
<td valign="top">

FALSE

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

2024-06-20 17:13:09.823

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

NULL

</td>
<td valign="top">

206745

</td>
<td valign="top">

Table-level

</td>
<td valign="top">

FALSE

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

2024-06-20 17:13:13.419

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

NULL

</td>
<td valign="top">

0

</td>
<td valign="top">

Table-level

</td>
<td valign="top">

FALSE

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

2024-06-20 17:13:16.402

</td>
<td valign="top">

0

</td>
<td valign="top">

2

</td>
<td valign="top">

1

</td>
<td valign="top">

NULL

</td>
<td valign="top">

0

</td>
<td valign="top">

Table-level

</td>
<td valign="top">

FALSE

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

0

</td>
<td valign="top">

512

</td>
<td valign="top">

2024-06-20 17:15:29.216

</td>
<td valign="top">

0

</td>
<td valign="top">

2295

</td>
<td valign="top">

2295

</td>
<td valign="top">

NULL

</td>
<td valign="top">

0

</td>
<td valign="top">

Table-level

</td>
<td valign="top">

FALSE

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
</tr>
</table>

**Related Information**  


[sp\_iqstatus System Procedure for Data Lake Relational Engine](sp-iqstatus-system-procedure-for-data-lake-relational-engine-a5b8569.md "Displays a variety of data lake Relational Engine status information about the current database.")

[sp\_iqversionuse System Procedure for Data Lake Relational Engine](sp-iqversionuse-system-procedure-for-data-lake-relational-engine-a5bd6f9.md "Displays version usage for the data lake Relational Engine main store.")

