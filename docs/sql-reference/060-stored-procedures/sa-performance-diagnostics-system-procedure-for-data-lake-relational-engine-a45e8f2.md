<!-- loioa45e8f2484f21015b094ea4ad73b88a6 -->

# sa\_performance\_diagnostics System Procedure for Data Lake Relational Engine

Returns a summary of request timing information for all connections when the database server has request timing logging enabled.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_performance_diagnostics( )
```



<a name="loioa45e8f2484f21015b094ea4ad73b88a6__section_i5q_t2s_mbb"/>

## Result Set


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

`Number`



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Returns the connection ID \(a number\) for the current connection.



</td>
</tr>
<tr>
<td valign="top">

`Name`



</td>
<td valign="top">

VARCHAR\(255\)



</td>
<td valign="top">

Returns the name of the current connection.

You can specify a connection name using the ConnectionName \(CON\) connection parameter.

The following names are used for temporary connections created by the database server:

-   INT:ApplyRecovery
-   INT:BackupDB
-   INT:Checkpoint
-   INT:Cleaner
-   INT:CloseDB
-   INT:CreateDB
-   INT:CreateMirror
-   INT:DelayedCommit
-   INT:DiagRcvr
-   INT:DropDB
-   INT:EncryptDB
-   INT:Exchange
-   INT:FlushMirrorLog
-   INT:FlushStats
-   INT:HTTPReq
-   INT:PromoteMirror
-   INT:PurgeSnapshot
-   INT:ReconnectMirror
-   INT:RecoverMirror
-   INT:RedoCheckpoint
-   INT:RefreshIndex
-   INT:ReloadTrigger
-   INT:RenameMirror
-   INT:RestoreDB
-   INT:StartDB
-   INT:VSS



</td>
</tr>
<tr>
<td valign="top">

`Userid`



</td>
<td valign="top">

VARCHAR\(255\)



</td>
<td valign="top">

Returns the user ID for the connection.



</td>
</tr>
<tr>
<td valign="top">

`DBNumber`



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Returns the ID number of the database.



</td>
</tr>
<tr>
<td valign="top">

`LoginTime`



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Returns the date and time the connection was established.



</td>
</tr>
<tr>
<td valign="top">

`TransactionStartTime`



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Returns a string containing the time the database was first modified after a COMMIT or ROLLBACK, or an empty string if no modifications have been made to the database since the last COMMIT or ROLLBACK.



</td>
</tr>
<tr>
<td valign="top">

`LastReqTime`



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Returns the time at which the last request for the specified connection started. This property can return an empty string for internal connections, such as events.



</td>
</tr>
<tr>
<td valign="top">

`ReqType`



</td>
<td valign="top">

VARCHAR\(255\)



</td>
<td valign="top">

Returns the type of the last request. If a connection has been cached by connection pooling, its ReqType value is CONNECT\_POOL\_CACHE.



</td>
</tr>
<tr>
<td valign="top">

`ReqStatus`



</td>
<td valign="top">

VARCHAR\(255\)



</td>
<td valign="top">

Returns the status of the request. It can be one of the following values:

-   Idle – the connection is not currently processing a request.
-   Unscheduled – the connection has work to do and is waiting for an available database server worker.
-   BlockedIO – the connection is blocked waiting for an I/O.
-   BlockedContention – the connection is blocked waiting for access to shared database server data structures.
-   BlockedLock – the connection is blocked waiting for a locked object.
-   Executing – the connection is executing a request.

The values marked with an asterisk \(\*\) are only returned when logging of request timing information has been turned on for the database server using the -zt server option. If request timing information is not being logged \(the default\), the values are reported as Executing.



</td>
</tr>
<tr>
<td valign="top">

`ReqTimeUnscheduled`



</td>
<td valign="top">

DOUBLE



</td>
<td valign="top">

Returns the amount of unscheduled time, or NULL if the -zt option was not specified.



</td>
</tr>
<tr>
<td valign="top">

`ReqTimeActive`



</td>
<td valign="top">

DOUBLE



</td>
<td valign="top">

Returns the amount of time, in seconds, spent processing requests, or NULL if the -zt option was not specified.



</td>
</tr>
<tr>
<td valign="top">

`ReqTimeBlockIO`



</td>
<td valign="top">

DOUBLE



</td>
<td valign="top">

Returns the amount of time, in seconds, spent waiting for I/O to complete, or NULL if the -zt option was not specified.



</td>
</tr>
<tr>
<td valign="top">

`ReqTimeBlockLock`



</td>
<td valign="top">

DOUBLE



</td>
<td valign="top">

Returns the amount of time, in seconds, spent waiting for a lock, or NULL if the -zt option was not specified.



</td>
</tr>
<tr>
<td valign="top">

`ReqTimeBlockContention`



</td>
<td valign="top">

DOUBLE



</td>
<td valign="top">

Returns the amount of time, in seconds, spent waiting for atomic access, or NULL if the RequestTiming server property is set to Off.



</td>
</tr>
<tr>
<td valign="top">

`ReqCountUnscheduled`



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Returns the number of times the connection waited for scheduling, or NULL if the -zt option was not specified.



</td>
</tr>
<tr>
<td valign="top">

`ReqCountActive`



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Returns the number of requests processed, or NULL if the RequestTiming server property is set to Off.



</td>
</tr>
<tr>
<td valign="top">

`ReqCountBlockIO`



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Returns the number of times the connection waited for I/O to complete, or NULL if the -zt option was not specified.



</td>
</tr>
<tr>
<td valign="top">

`ReqCountBlockLock`



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Returns the number of times the connection waited for a lock, or NULL if the -zt option was not specified.



</td>
</tr>
<tr>
<td valign="top">

`ReqCountBlockContention`



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Returns the number of times the connection waited for atomic access, or NULL if the -zt option was not specified.



</td>
</tr>
<tr>
<td valign="top">

`LastIdle`



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Returns the number of ticks between requests.



</td>
</tr>
<tr>
<td valign="top">

`BlockedOn`



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Returns zero if the current connection isn't blocked, or if it is blocked, the connection number on which the connection is blocked because of a locking conflict.



</td>
</tr>
<tr>
<td valign="top">

`UncommitOp`



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Returns the number of uncommitted operations.



</td>
</tr>
<tr>
<td valign="top">

`CurrentProcedure`



</td>
<td valign="top">

VARCHAR\(255\)



</td>
<td valign="top">

Returns the name of the procedure that a connection is currently executing. If the connection is executing nested procedure calls, the name is the name of the current procedure. If there is no procedure executing, an empty string is returned.



</td>
</tr>
<tr>
<td valign="top">

`EventName`



</td>
<td valign="top">

VARCHAR\(255\)



</td>
<td valign="top">

Returns the name of the associated event if the connection is running an event handler. Otherwise, an empty string is returned.



</td>
</tr>
<tr>
<td valign="top">

`CurrentLineNumber`



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Returns the current line number of the procedure or compound statement a connection is executing. The procedure can be identified using the CurrentProcedure property. If the line is part of a compound statement from the client, an empty string is returned.



</td>
</tr>
<tr>
<td valign="top">

`LastStatement`



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

Returns the most recently prepared SQL statement for the current connection.

The LastStatement value is set when a statement is prepared, and is cleared when a statement is dropped. Only one statement string is remembered for each connection.

If sa\_conn\_activity reports a non-empty value for a connection, it is most likely the statement that the connection is currently executing. If the statement had completed, it would likely have been dropped and the property value would have been cleared. If an application prepares multiple statements and retains their statement handles, then the LastStatement value does not reflect what a connection is currently doing.

When client statement caching is enabled, and a cached statement is reused, this property returns an empty string.



</td>
</tr>
<tr>
<td valign="top">

`LastPlanText`



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

Returns the long text plan of the last query executed on the connection. You control the remembering of the last plan by setting the RememberLastPlan option of the sa\_server\_option system procedure, or using the -zp server option.



</td>
</tr>
<tr>
<td valign="top">

`AppInfo`



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

Returns information about the client that made the connection. For HTTP connections, this includes information about the browser. For connections using older versions of jConnect or Open Client, the information may be incomplete.

The API value can be DBLIB, ODBC, OLEDB, ADO.NET, iAnywhereJDBC, PHP, PerlDBD, or DBEXPRESS.



</td>
</tr>
<tr>
<td valign="top">

`LockCount`



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Returns the number of locks held by the connection.



</td>
</tr>
<tr>
<td valign="top">

`SnapshotCount`



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Returns the number of snapshots associated with the connection.



</td>
</tr>
</table>



<a name="loioa45e8f2484f21015b094ea4ad73b88a6__section_f1s_dfs_mbb"/>

## Remarks

The `sa_performance_diagnostics` system procedure returns a result set consisting of a set of request timing properties and statistics if the server has been told to collect the information. Recording of request timing information must be turned on the database server before calling `sa_performance_diagnostics`. To do this, specify the -zt option when starting the database server or execute the following:

```
CALL sa_server_option( 'RequestTiming','ON' );
```



<a name="loioa45e8f2484f21015b094ea4ad73b88a6__iq_iquda_113"/>

## Privileges

To run this procedure, you need the EXECUTE privilege on the procedure. See [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md). You must also have the MONITOR system privilege.



<a name="loioa45e8f2484f21015b094ea4ad73b88a6__section_jtq_wss_mbb"/>

## Side Effects

None



<a name="loioa45e8f2484f21015b094ea4ad73b88a6__iq_iquda_114"/>

## Examples

-   The following query identifies connections that have spent a long time waiting for database server requests to complete.

    ```
    SELECT Number, Name, 
          CAST( DATEDIFF( second, LoginTime, CURRENT TIMESTAMP ) AS DOUBLE ) AS T, 
          IF T <>
    ```

-   The following example finds all requests that are currently executing, and have been executing for more than 60 seconds:

    ```
    SELECT Number, Name, 
           CAST( DATEDIFF( second, LastReqTime, CURRENT TIMESTAMP ) AS DOUBLE ) AS ReqTime 
    FROM sa_performance_diagnostics() 
    WHERE ReqStatus <> 'IDLE' AND ReqTime > 60.0 
    ORDER BY ReqTime DESC;
    ```


