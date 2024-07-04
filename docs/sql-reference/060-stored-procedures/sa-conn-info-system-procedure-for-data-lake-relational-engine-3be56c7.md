<!-- loio3be56c746c5f10148ef0b7a3d2a40f18 -->

# sa\_conn\_info System Procedure for Data Lake Relational Engine

Reports connection property information.



<a name="loio3be56c746c5f10148ef0b7a3d2a40f18__section_idn_b13_b4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_conn_info( [ <connidparm> ] )
```



## Parameters


<dl>
<dt><b>

*<connidparm\>* 

</b></dt>
<dd>

This optional INTEGER parameter specifies the connection ID number. The default is NULL.



</dd>
</dl>



## Result Set


<table>
<tr>
<th valign="top">

Column name

</th>
<th valign="top">

Data type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Number

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

Name

</td>
<td valign="top">

VARCHAR\(255\)

</td>
<td valign="top">

Returns an identifier \(string\) for the current connection.

Temporary connection names have `INT:` prepended to the connection name.

</td>
</tr>
<tr>
<td valign="top">

Userid

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

DBNumber

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

LastReqTime

</td>
<td valign="top">

VARCHAR\(255\)

</td>
<td valign="top">

Returns the time at which the last request for the specified connection started, in the timezone of the database. This property can return an empty string for internal connections, such as events.

</td>
</tr>
<tr>
<td valign="top">

ReqType

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

CommLink

</td>
<td valign="top">

VARCHAR\(255\)

</td>
<td valign="top">

Returns the communication link for the connection. This is one of the network protocols supported by data lake Relational Engine, or local for a same-computer connection.

</td>
</tr>
<tr>
<td valign="top">

NodeAddr

</td>
<td valign="top">

VARCHAR\(255\)

</td>
<td valign="top">

Returns the address of the client in a client/server connection.

</td>
</tr>
<tr>
<td valign="top">

ClientPort

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Returns the client's TCP/IP port number or 0 if the connection isn't a TCP/IP connection.

</td>
</tr>
<tr>
<td valign="top">

ServerPort

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Returns the database server's TCP/IP port number or 0.

</td>
</tr>
<tr>
<td valign="top">

BlockedOn

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

LockRowID

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

Returns the identifier of the locked row.

LockRowID is NULL if the connection is not waiting on a lock associated with a row \(that is, it is not waiting on a lock, or it is waiting on a lock that has no associated row\).

</td>
</tr>
<tr>
<td valign="top">

LockIndexID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Returns the identifier of the locked index.

LockIndexID is -1 if the lock is associated with all indexes on the table in LockTable. LockIndexID is NULL if the connection is not waiting on a lock associated with an index \(that is, it is not waiting on a lock, or it is waiting on a lock that has no associated index\).

</td>
</tr>
<tr>
<td valign="top">

LockTable

</td>
<td valign="top">

VARCHAR\(255\)

</td>
<td valign="top">

Returns the name of the table associated with a lock if the connection is currently waiting for a lock. The LockTable value is an empty string if there is no lock, or if the object associated with the lock is not a table.

</td>
</tr>
<tr>
<td valign="top">

UncommitOps

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

ParentConnection

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Returns the connection ID of the connection that created a temporary connection to perform a database operation \(such as performing a backup or creating a database\). For other types of connections, this property returns NULL.

</td>
</tr>
<tr>
<td valign="top">

LockObject

</td>
<td valign="top">

VARCHAR\(255\)

</td>
<td valign="top">

Returns the name of the object associated with the lock for which the connection is waiting, if any. If the object is a table, this value is the same as the LockTable value. LockObject is NULL if the connection is not waiting for a lock.

</td>
</tr>
<tr>
<td valign="top">

LockObjectType

</td>
<td valign="top">

CHAR\(20\)

</td>
<td valign="top">

Returns the type of the object associated with the lock for which the connection is waiting, if any. LockObjectType is NULL if the connection is not waiting for a lock.

</td>
</tr>
</table>



## Remarks

If *<connidparm\>* is less than zero, then a result set consisting of connection properties for the current connection is returned. If *<connidparm\>* is not supplied or is NULL, then connection properties are returned for all connections to all databases running on the database server.

In a block situation, the BlockedOn value returned by this procedure allows you to check which users are blocked, and who they are blocked on. The sa\_locks system procedure can be used to display the locks held by the blocking connection.

For more information based on any of these properties, you can execute something similar to the following:

```
SELECT *, DB_NAME( DBNumber ),
   CONNECTION_PROPERTY( 'LastStatement', Number )
   FROM sa_conn_info( )
```

The value of LockRowID can be used to look up a lock in the output of the sa\_locks procedure.

The value in LockIndexID can be used to look up a lock in the output of the sa\_locks procedure. Also, the value in LockIndexID corresponds to the primary key of the ISYSIDX system table, which can be viewed using the SYSIDX system view.

Every lock has an associated table, so the value of LockTable can be used to unambiguously determine whether a connection is waiting on a lock.



## Privileges

Requires EXECUTE object-level privilege on this procedure. To obtain a list of all connection IDs, you also need the MONITOR system privilege.



## Side Effects

None.



## Examples

This example returns a result set summarizing connection properties for all connections to the server.

```
CALL sa_conn_info( );
```


<table>
<tr>
<th valign="top">

Number

</th>
<th valign="top">

Name

</th>
<th valign="top">

Userid

</th>
<th valign="top">

DBNumber

</th>
<th valign="top">

...

</th>
</tr>
<tr>
<td valign="top">

79

</td>
<td valign="top">

SQL\_DBC\_10dcf810

</td>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

0

</td>
<td valign="top">

...

</td>
</tr>
<tr>
<td valign="top">

46

</td>
<td valign="top">

setup

</td>
<td valign="top">

User1

</td>
<td valign="top">

0

</td>
<td valign="top">

...

</td>
</tr>
<tr>
<td valign="top">

...

</td>
<td valign="top">

...

</td>
<td valign="top">

...

</td>
<td valign="top">

...

</td>
<td valign="top">

...

</td>
</tr>
</table>

This example returns the number of blocked connections.

```
SELECT COUNT(*) FROM sa_conn_info() WHERE blockedOn = connection_property('number');
```

