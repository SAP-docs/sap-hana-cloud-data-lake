<!-- loio3c1f80b46c5f101481d894f2bdad55da -->

# SAIsolationLevel Enumeration

Specifies database server isolation levels.



Visual Basic
:   ```
Public Enum SAIsolationLevel
```

C\#
:   ```
enum SAIsolationLevel
```



## Members


<table>
<tr>
<th valign="top">

Member name



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

Chaos



</td>
<td valign="top">

This isolation level is unsupported.

If you call SAConnection.BeginTransaction with this isolation level, then an exception is thrown.

For more information, see "BeginTransaction method".



</td>
</tr>
<tr>
<td valign="top">

ReadCommitted



</td>
<td valign="top">

Sets the behavior to be equivalent to isolation level 1.

This isolation level prevents dirty reads, but allows non-repeatable reads and phantom rows.

For more information, see "Isolation levels and consistency".



</td>
</tr>
<tr>
<td valign="top">

ReadUncommitted



</td>
<td valign="top">

Sets the behavior to be equivalent to isolation level 0.

This isolation level allows dirty reads, non-repeatable reads, and phantom rows.

For more information, see "Isolation levels and consistency".



</td>
</tr>
<tr>
<td valign="top">

RepeatableRead



</td>
<td valign="top">

Sets the behavior to be equivalent to isolation level 2.

This isolation level prevents dirty reads and guarantees repeatable reads. However, it allows phantom rows.

For more information, see "Isolation levels and consistency".



</td>
</tr>
<tr>
<td valign="top">

Serializable



</td>
<td valign="top">

Sets the behavior to be equivalent to isolation level 3.

This isolation level prevents dirty reads, guarantees repeatable reads, and prevents phantom rows.

For more information, see "Isolation levels and consistency".



</td>
</tr>
<tr>
<td valign="top">

Snapshot



</td>
<td valign="top">

Uses a snapshot of committed data from the time when the first row is read, inserted, updated, or deleted by the transaction.

This isolation level uses a snapshot of committed data from the time when the first row is read or updated by the transaction.

For more information, see "Isolation levels and consistency".



</td>
</tr>
<tr>
<td valign="top">

Unspecified



</td>
<td valign="top">

This isolation level is unsupported.

If you call SAConnection.BeginTransaction with this isolation level, then an exception is thrown.

For more information, see "BeginTransaction method".



</td>
</tr>
<tr>
<td valign="top">

ReadOnlySnapshot



</td>
<td valign="top">

For read-only statements, use a snapshot of committed data from the time when the first row is read from the database.

Non-repeatable reads and phantom rows can occur within a transaction, but not within a single statement. For updatable statements, use the isolation level specified by the updatable\_statement\_isolation option \(can be one of 0 \(the default\), 1, 2, or 3\).

For more information, see "Isolation levels and consistency".



</td>
</tr>
<tr>
<td valign="top">

StatementSnapshot



</td>
<td valign="top">

Use a snapshot of committed data from the time when the first row is read by the statement.

Each statement within the transaction sees a snapshot of data from a different time.

For each statement, use a snapshot of committed data from the time when the first row is read from the database. Non-repeatable reads and phantom rows can occur within a transaction, but not within a single statement.

For more information, see "Isolation levels and consistency".



</td>
</tr>
</table>



## Remarks

This class augments the System.Data.IsolationLevel class.

The .NET Data Provider supports all database server isolation levels, including the snapshot isolation levels. To use snapshot isolation, specify one of SAIsolationLevel.Snapshot, SAIsolationLevel.ReadOnlySnapshot, or SAIsolationLevel.StatementSnapshot as the parameter to BeginTransaction. BeginTransaction has been overloaded so it can take either an IsolationLevel or an SAIsolationLevel. The values in the two enumerations are the same, except for ReadOnlySnapshot and StatementSnapshot which exist only in SAIsolationLevel. There is a new property in SATransaction called SAIsolationLevel that gets the SAIsolationLevel.

For more information, see "Snapshot isolation".

