<!-- loio3bc695906c5f10148aaabe9d8f52d0e5 -->

# List of Connection Properties

Connection properties are available for each connection to a database. Connection property names are case insensitive. Use the CONNECTION\_PROPERTY system function or the sa\_conn\_properties system procedure to retrieve connection properties.



## Example

The following statement returns the number of pages that have been read from file by the current connection.

```
SELECT CONNECTION_PROPERTY ( 'DiskRead' );
```

Use the sa\_conn\_properties system procedure to retrieve the values of all connection properties:

```
CALL sa_conn_properties( );
```



## Connection Properties


<table>
<tr>
<th valign="top">

Property name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

allow\_nulls\_by\_default

</td>
<td valign="top">

Whether columns created without specifying either NULL or NOT NULL are allowed to contain NULL values. This property corresponds to the allow\_nulls\_by\_default option for the connection.

</td>
</tr>
<tr>
<td valign="top">

allow\_read\_client\_file

</td>
<td valign="top">

Whether the database server allows the reading of files on a client computer. This property corresponds to the allow\_read\_client\_file option for the connection.

</td>
</tr>
<tr>
<td valign="top">

allow\_snapshot\_isolation

</td>
<td valign="top">

Whether snapshot isolation is enabled or disabled. This property corresponds to the allow\_snapshot\_isolation option for the connection.

</td>
</tr>
<tr>
<td valign="top">

allow\_write\_client\_file

</td>
<td valign="top">

Whether the database server allows the writing of files to a client computer. This property corresponds to the allow\_write\_client\_file option for the connection.

</td>
</tr>
<tr>
<td valign="top">

ansi\_blanks

</td>
<td valign="top">

Indicates when character data is truncated at the client side. This property corresponds to ansi\_blanks option for the connection.

</td>
</tr>
<tr>
<td valign="top">

ansi\_close\_cursors\_on\_rollback

</td>
<td valign="top">

Whether cursors opened WITH HOLD are closed when a ROLLBACK is performed. This property corresponds to the ansi\_close\_cursors\_on\_rollback option for the connection.

</td>
</tr>
<tr>
<td valign="top">

ansi\_permissions

</td>
<td valign="top">

Whether privileges are checked for DELETE and UPDATE statements. This property corresponds to the ansi\_permissions option for the connection.

</td>
</tr>
<tr>
<td valign="top">

ansi\_substring

</td>
<td valign="top">

The behavior of the SUBSTRING \(SUBSTR\) function when negative values are provided for the start or length parameters. This property corresponds to the ansi\_substring option for the connection.

</td>
</tr>
<tr>
<td valign="top">

ansi\_update\_constraints

</td>
<td valign="top">

The range of updates that are permitted. This property corresponds to the ansi\_update\_constraints option for the connection.

</td>
</tr>
<tr>
<td valign="top">

ansinull

</td>
<td valign="top">

How NULL values are interpreted. This property corresponds to the ansinull option.

</td>
</tr>
<tr>
<td valign="top">

AppInfo

</td>
<td valign="top">

Information about the client that made the connection. For HTTP connections, this includes information about the browser. For connections using older versions of SAP Open Client or jConnect, the information may be incomplete.

</td>
</tr>
<tr>
<td valign="top">

ApproximateCPUTime

</td>
<td valign="top">

The estimate of the amount of CPU time accumulated by a given connection, in seconds. The value returned may differ from the actual value by as much as 50%, although typical variations are in the 5-10% range. On multi-processor computers, each CPU \(or hyperthread or core\) accumulates time, so the sum of accumulated times for all connections may be greater than the elapsed time.

</td>
</tr>
<tr>
<td valign="top">

audit\_log

</td>
<td valign="top">

The location where audit logs are directed.

</td>
</tr>
<tr>
<td valign="top">

auditing

</td>
<td valign="top">

Whether auditing is enabled for the database\(On\) or not \(Off\). This option corresponds to the auditing option.

</td>
</tr>
<tr>
<td valign="top">

auditing\_options

</td>
<td valign="top">

This property is reserved for system use.

</td>
</tr>
<tr>
<td valign="top">

Authenticated

</td>
<td valign="top">

Whether the application sent a valid connection authentication string \(Yes\) or not \(No\).

</td>
</tr>
<tr>
<td valign="top">

AuthType

</td>
<td valign="top">

The type of authentication used when connecting. The value returned is Standard or an empty string. The value is an empty string when the connection is an internal connection or for connections for HTTP services that use AUTHORIZATION OFF.

</td>
</tr>
<tr>
<td valign="top">

autocommit\_ddl

</td>
<td valign="top">

Whether transactional DDL is enabled on the database.

</td>
</tr>
<tr>
<td valign="top">

auto\_commit

</td>
<td valign="top">

Whether the database server automatically commits after each statement. By default, the database server operates in manual commit mode. To turn on automatic commits, set the auto\_commit database option \(a server-side option\). Do not confuse this option with the Interactive SQL option of the same name.autocommit\_ddl must be disabled \(ON\) before enabling auto\_commit. 

</td>
</tr>
<tr>
<td valign="top">

auto\_commit\_on\_create\_local\_temp\_index

</td>
<td valign="top">

Whether the database server performs a COMMIT before an index is created on a local temporary table. This property corresponds to the value of the auto\_commit\_on\_create\_local\_temp\_index option.

</td>
</tr>
<tr>
<td valign="top">

background\_priority

</td>
<td valign="top">

This property is deprecated. The value of the background\_priority option for the connection, which indicates how much impact the current connection has on the performance of other connections.

</td>
</tr>
<tr>
<td valign="top">

BlockedOn

</td>
<td valign="top">

Whether the current connection is blocked or not \(zero\). When the connection is blocked because of a locking conflict, the value is the connection number on which the connection is blocked.

</td>
</tr>
<tr>
<td valign="top">

blocking

</td>
<td valign="top">

The database server's behavior in response to locking conflicts. This property corresponds to the blocking option for the connection.

</td>
</tr>
<tr>
<td valign="top">

blocking\_others\_timeout

</td>
<td valign="top">

The length of time that another connection can block on the current connection's row and table locks before the current connection is rolled back. This property corresponds to the value of the blocking\_others\_timeout option.

</td>
</tr>
<tr>
<td valign="top">

blocking\_timeout

</td>
<td valign="top">

The length of time, in milliseconds, a transaction waits to obtain a lock. This property corresponds to the blocking\_timeout option.

</td>
</tr>
<tr>
<td valign="top">

BytesReceived

</td>
<td valign="top">

The number of bytes received during client/server communications. This value is updated for HTTP and HTTPS connections.

</td>
</tr>
<tr>
<td valign="top">

BytesReceivedUncomp

</td>
<td valign="top">

The number of bytes that would have been received during client/server communications if compression was disabled. This value is the same as the value for BytesReceived if compression is disabled.

</td>
</tr>
<tr>
<td valign="top">

BytesSent

</td>
<td valign="top">

The number of bytes sent during client/server communications. This value is updated for HTTP and HTTPS connections.

</td>
</tr>
<tr>
<td valign="top">

BytesSentUncomp

</td>
<td valign="top">

The number of bytes that would have been sent during client/server communications if compression was disabled. This value is the same as the value for BytesSent if compression is disabled.

</td>
</tr>
<tr>
<td valign="top">

CacheHits

</td>
<td valign="top">

The number of successful reads of the cache.

</td>
</tr>
<tr>
<td valign="top">

CacheRead

</td>
<td valign="top">

The number of database pages that have been looked up in the cache.

</td>
</tr>
<tr>
<td valign="top">

CacheReadIndInt

</td>
<td valign="top">

The number of index internal-node pages that have been read from the cache.

</td>
</tr>
<tr>
<td valign="top">

CacheReadIndLeaf

</td>
<td valign="top">

The number of index leaf pages that have been read from the cache.

</td>
</tr>
<tr>
<td valign="top">

CacheReadTable

</td>
<td valign="top">

The number of table pages that have been read from the cache.

</td>
</tr>
<tr>
<td valign="top">

CacheReadWorkTable

</td>
<td valign="top">

The number of cache work table reads.

</td>
</tr>
<tr>
<td valign="top">

CarverHeapPages

</td>
<td valign="top">

The number of heap pages used for short-term purposes such as query optimization.

</td>
</tr>
<tr>
<td valign="top">

chained

</td>
<td valign="top">

The value of the chained option, which indicates the transaction mode used in the absence of a BEGIN TRANSACTION statement.

</td>
</tr>
<tr>
<td valign="top">

CharSet

</td>
<td valign="top">

The CHAR character set used by the connection. This property has extensions that you can specify when querying the property value.

</td>
</tr>
<tr>
<td valign="top">

checkpoint\_time

</td>
<td valign="top">

The value of the checkpoint\_time option, which indicates the maximum time, in minutes, that the database server runs without doing a checkpoint.

</td>
</tr>
<tr>
<td valign="top">

cis\_option

</td>
<td valign="top">

Specifies 7 if debugging information for remote data access appears in the database server messages window. Specifies 0 if the debugging information for remote data access does not appear in the database server messages window. This property corresponds to the cis\_option option.

</td>
</tr>
<tr>
<td valign="top">

cis\_rowset\_size

</td>
<td valign="top">

The number of rows that are returned from remote servers for each fetch. This property corresponds to the value of the cis\_rowset\_size option.

</td>
</tr>
<tr>
<td valign="top">

ClientLibrary

</td>
<td valign="top">

The connection library type. The value is jConnect for jConnect connections; CT\_Library for SAP Open Client connections; None for HTTP connections, and CmdSeq for ODBC, Embedded SQL, OLE DB, ADO.NET, and SAP IQ JDBC driver connections.

</td>
</tr>
<tr>
<td valign="top">

ClientNodeAddress

</td>
<td valign="top">

The node for the client in a client/server connection. When the client and server are both on the same computer, an empty string is returned. This property is a synonym for the NodeAddress property.

The value is *NA* if the request that is currently executing is part of an event handler.

</td>
</tr>
<tr>
<td valign="top">

ClientPort

</td>
<td valign="top">

The client's TCP/IP port number or 0 if the connection isn't a TCP/IP connection.

</td>
</tr>
<tr>
<td valign="top">

ClientStmtCacheHits

</td>
<td valign="top">

The number of prepares that were not required for this connection because of the client statement cache. This value is the number of additional prepares that would be required if client statement caching was disabled.

</td>
</tr>
<tr>
<td valign="top">

ClientStmtCacheMisses

</td>
<td valign="top">

The number of statements in the client statement cache for this connection that were prepared again. This value is the number of times a cached statement was considered for reuse, but could not be reused because of a schema change, a database option setting, or a DROP VARIABLE statement.

</td>
</tr>
<tr>
<td valign="top">

close\_on\_endtrans

</td>
<td valign="top">

Whether cursors are closed at the end of a transaction. This property corresponds to the close\_on\_endtrans option.

</td>
</tr>
<tr>
<td valign="top">

collect\_statistics\_on\_dml\_updates

</td>
<td valign="top">

Whether statistics are gathered during the execution of data-altering DML statements such as INSERT, DELETE, and UPDATE. This property corresponds to the collect\_statistics\_on\_dml\_updates option.

</td>
</tr>
<tr>
<td valign="top">

Commit

</td>
<td valign="top">

The number of Commit requests that have been handled.

</td>
</tr>
<tr>
<td valign="top">

CommLink

</td>
<td valign="top">

The communication link for the connection. The value is one of the supported network protocols supported, or *local* for a same-computer connection. The value is *NA* if the request that is currently executing is part of an event handler.

</td>
</tr>
<tr>
<td valign="top">

CommNetworkLink

</td>
<td valign="top">

The communication link for the connection. This value returned is one of the supported network protocols. Values include SharedMemory and TCPIP. The value always includes the name of the link, regardless of whether it is same-computer or not. The value is *NA* if the request that is currently executing is part of an event handler.

</td>
</tr>
<tr>
<td valign="top">

CommProtocol

</td>
<td valign="top">

The communication protocol. The value is TDS for SAP Open Client and jConnect connections, HTTP for HTTP connections, HTTPS for HTTPS connections. The value is CmdSeq for ODBC, Embedded SQL, OLE DB, ADO.NET, and SAP IQ JDBC driver connections.

</td>
</tr>
<tr>
<td valign="top">

Compression

</td>
<td valign="top">

Whether communication compression is enabled on the connection. The value is *NA* if the request that is currently executing is part of an event handler.

</td>
</tr>
<tr>
<td valign="top">

conn\_auditing

</td>
<td valign="top">

Whether auditing is enabled or disabled for the connection when the auditing option is also set to *On*. This property corresponds to the conn\_auditing option.

</td>
</tr>
<tr>
<td valign="top">

ConnectedTime

</td>
<td valign="top">

The total length of time, in seconds, that a connection has been connected.

</td>
</tr>
<tr>
<td valign="top">

connection\_authentication

</td>
<td valign="top">

The string used to authenticate the client. Authentication is required before the database can be modified. This property corresponds to the connection\_authentication option.

</td>
</tr>
<tr>
<td valign="top">

connection\_type

</td>
<td valign="top">

The value of the connection\_type database option: one of: Event, Internal, Standard, or Monitor

</td>
</tr>
<tr>
<td valign="top">

continue\_after\_raiserror

</td>
<td valign="top">

Whether execution of a procedure or trigger is stopped whenever the RAISERROR statement is encountered. This property corresponds to the continue\_after\_raiserror option

</td>
</tr>
<tr>
<td valign="top">

conversion\_error

</td>
<td valign="top">

Whether data type conversion failures are reported when fetching information from the database. This property corresponds to the value of the conversion\_error option.

</td>
</tr>
<tr>
<td valign="top">

cooperative\_commit\_timeout

</td>
<td valign="top">

This property is deprecated. The value of the cooperative\_commit\_timeout option, which is the time, in milliseconds, that the database server waits for other connections to fill a page of the log before writing to disk.

</td>
</tr>
<tr>
<td valign="top">

cooperative\_commits

</td>
<td valign="top">

This property is deprecated. The value of the cooperative\_commits option, which is On or Off to indicate when commits are written to disk.

</td>
</tr>
<tr>
<td valign="top">

CurrentLineNumber

</td>
<td valign="top">

The current line number of the procedure or compound statement a connection is executing. The procedure can be identified using the CurrentProcedure property. If the line is part of a compound statement from the client, an empty string is returned.

</td>
</tr>
<tr>
<td valign="top">

CurrentProcedure

</td>
<td valign="top">

The name of the procedure that a connection is currently executing. If the connection is executing nested procedure calls, the name is the name of the current procedure. If there is no procedure executing, an empty string is returned.

</td>
</tr>
<tr>
<td valign="top">

Cursor

</td>
<td valign="top">

The number of declared cursors that are currently being maintained by the database server.

</td>
</tr>
<tr>
<td valign="top">

CursorOpen

</td>
<td valign="top">

The number of open cursors that are currently being maintained by the database server.

</td>
</tr>
<tr>
<td valign="top">

database\_authentication

</td>
<td valign="top">

Indicates the string used to authenticate the database. Authentication is required for authenticated database servers before the database can be modified. This property corresponds to the database\_authentication option

</td>
</tr>
<tr>
<td valign="top">

date\_format

</td>
<td valign="top">

The value of the date\_format option, which is a string indicating the format for dates retrieved from the database.

</td>
</tr>
<tr>
<td valign="top">

date\_order

</td>
<td valign="top">

The value of the date\_order option, which is a string indicating how dates are formatted.

</td>
</tr>
<tr>
<td valign="top">

DBNumber

</td>
<td valign="top">

The ID number of the database.

</td>
</tr>
<tr>
<td valign="top">

db\_publisher

</td>
<td valign="top">

The user ID of the database publisher. This property corresponds to the db\_publisher option.

</td>
</tr>
<tr>
<td valign="top">

debug\_messages

</td>
<td valign="top">

Whether MESSAGE statements that include a DEBUG ONLY clause are executed. This property corresponds to the debug\_messages option

</td>
</tr>
<tr>
<td valign="top">

dedicated\_task

</td>
<td valign="top">

Whether a request handling task is dedicated exclusively to handling requests for the connection. This property corresponds to the dedicated\_task option

</td>
</tr>
<tr>
<td valign="top">

default\_dbspace

</td>
<td valign="top">

The name of the default dbspace, or an empty string if the default dbspace has not been specified. This property corresponds to the default\_dbspace option,

</td>
</tr>
<tr>
<td valign="top">

default\_timestamp\_increment

</td>
<td valign="top">

The number of microseconds that is added to a column of type TIMESTAMP to keep values in the column unique. This property corresponds to the default\_timestamp\_increment.

</td>
</tr>
<tr>
<td valign="top">

delayed\_commit\_timeout

</td>
<td valign="top">

The time, in milliseconds, that the database server waits to return control to an application following a COMMIT. This property corresponds to the delayed\_commit\_timeout option.

</td>
</tr>
<tr>
<td valign="top">

delayed\_commits

</td>
<td valign="top">

Whether the database server returns control to an application following a COMMIT or not. This property corresponds to the delayed\_commits option.

</td>
</tr>
<tr>
<td valign="top">

DiskRead

</td>
<td valign="top">

The number of pages that have been read from disk.

</td>
</tr>
<tr>
<td valign="top">

DiskReadHint

</td>
<td valign="top">

The number of disk read hints.

</td>
</tr>
<tr>
<td valign="top">

DiskReadHintPages

</td>
<td valign="top">

The number of disk read hint pages.

</td>
</tr>
<tr>
<td valign="top">

DiskReadIndInt

</td>
<td valign="top">

The number of index internal-node pages that have been read from disk.

</td>
</tr>
<tr>
<td valign="top">

DiskReadIndLeaf

</td>
<td valign="top">

The number of index leaf pages that have been read from disk.

</td>
</tr>
<tr>
<td valign="top">

DiskReadTable

</td>
<td valign="top">

The number of table pages that have been read from disk.

</td>
</tr>
<tr>
<td valign="top">

DiskReadWorkTable

</td>
<td valign="top">

The number of disk work table reads.

</td>
</tr>
<tr>
<td valign="top">

disk\_sandbox

</td>
<td valign="top">

Whether the read-write file operations of the database are restricted to the directory where the main database file is located. This property corresponds to the disk\_sandbox option.

</td>
</tr>
<tr>
<td valign="top">

DiskSyncRead

</td>
<td valign="top">

The number of disk reads issued synchronously.

</td>
</tr>
<tr>
<td valign="top">

DiskSyncWrite

</td>
<td valign="top">

The number of writes issued synchronously.

</td>
</tr>
<tr>
<td valign="top">

DiskWaitRead

</td>
<td valign="top">

The number of times the database server waited for an asynchronous read.

</td>
</tr>
<tr>
<td valign="top">

DiskWaitWrite

</td>
<td valign="top">

The number of times the database server waited for an asynchronous write.

</td>
</tr>
<tr>
<td valign="top">

DiskWrite

</td>
<td valign="top">

The number of modified pages that have been written to disk.

</td>
</tr>
<tr>
<td valign="top">

DiskWriteHint

</td>
<td valign="top">

The number of disk write hints.

</td>
</tr>
<tr>
<td valign="top">

DiskWriteHintPages

</td>
<td valign="top">

The number of disk write hint pages.

</td>
</tr>
<tr>
<td valign="top">

divide\_by\_zero\_error

</td>
<td valign="top">

Whether if division by zero results in an error \(On\) or not \(Off\). This property corresponds to the divide\_by\_zero\_error option.

</td>
</tr>
<tr>
<td valign="top">

Encryption

</td>
<td valign="top">

Whether the connection is encrypted or not. The values are None, Simple, rsa\_tls, or rsa\_tls\_fips.

</td>
</tr>
<tr>
<td valign="top">

escape\_character

</td>
<td valign="top">

This property is reserved for system use. Do not change the setting of this option.

</td>
</tr>
<tr>
<td valign="top">

EventName

</td>
<td valign="top">

The name of the associated event if the connection is running an event handler. Otherwise, an empty string is returned.

</td>
</tr>
<tr>
<td valign="top">

exclude\_operators

</td>
<td valign="top">

This property is reserved for system use. Do not change the setting of this option.

</td>
</tr>
<tr>
<td valign="top">

ExprCacheAbandons

</td>
<td valign="top">

The number of times that the expression cache was abandoned because the hit rate was too low.

</td>
</tr>
<tr>
<td valign="top">

ExprCacheDropsToReadOnly

</td>
<td valign="top">

The number of times that the expression cache dropped to read-only status because the hit rate was low.

</td>
</tr>
<tr>
<td valign="top">

ExprCacheEvicts

</td>
<td valign="top">

The number of evictions from the expression cache.

</td>
</tr>
<tr>
<td valign="top">

ExprCacheHits

</td>
<td valign="top">

The number of hits in the expression cache.

</td>
</tr>
<tr>
<td valign="top">

ExprCacheInserts

</td>
<td valign="top">

The number of values inserted into the expression cache.

</td>
</tr>
<tr>
<td valign="top">

ExprCacheLookups

</td>
<td valign="top">

The number of lookups done in the expression cache.

</td>
</tr>
<tr>
<td valign="top">

ExprCacheResumesOfReadWrite

</td>
<td valign="top">

The number of times that the expression cache resumed read-write status because the hit rate increased.

</td>
</tr>
<tr>
<td valign="top">

ExprCacheStarts

</td>
<td valign="top">

The number of times that the expression cache was started.

</td>
</tr>
<tr>
<td valign="top">

extern\_login\_credentials

</td>
<td valign="top">

Whether remote connections are attempted using the logged in user's external login credentials or the effective user's external login credentials. This property corresponds to the extern\_login\_credentials option.

</td>
</tr>
<tr>
<td valign="top">

extended\_join\_syntax

</td>
<td valign="top">

Whether queries with duplicate correlation name syntax for multi-table joins are allowed, or whether they are reported as errors. This property corresponds to the extended\_join\_syntax option.

</td>
</tr>
<tr>
<td valign="top">

fire\_triggers

</td>
<td valign="top">

Whether triggers are fired in the database. This property corresponds to the fire\_triggers option.

</td>
</tr>
<tr>
<td valign="top">

first\_day\_of\_week

</td>
<td valign="top">

The number that is used for the first day of the week, where 7=Sunday and 1=Monday. This property corresponds to the first\_day\_of\_week option.

</td>
</tr>
<tr>
<td valign="top">

for\_xml\_null\_treatment

</td>
<td valign="top">

The value is Omit if elements and attributes that contain NULL values are omitted from the result. The value is Empty if empty elements or attributes are generated for NULL values when the FOR XML clause is used in a query. This property corresponds to the for\_xml\_null\_treatment option.

</td>
</tr>
<tr>
<td valign="top">

force\_view\_creation

</td>
<td valign="top">

This property is reserved for system use. Do not change the setting of this option.

</td>
</tr>
<tr>
<td valign="top">

FullCompare

</td>
<td valign="top">

The number of comparisons that have been performed beyond the hash value in an index.

</td>
</tr>
<tr>
<td valign="top">

GetData

</td>
<td valign="top">

The number of GETDATA requests.

</td>
</tr>
<tr>
<td valign="top">

global\_database\_id

</td>
<td valign="top">

The starting value used for columns created with DEFAULT GLOBAL AUTOINCREMENT. This property corresponds to the global\_database\_id option.

</td>
</tr>
<tr>
<td valign="top">

HashForcedPartitions

</td>
<td valign="top">

The number of times that a hash operator was forced to partition because of competition for memory.

</td>
</tr>
<tr>
<td valign="top">

HashRowsFiltered

</td>
<td valign="top">

The number of probe rows rejected by bit-vector filters.

</td>
</tr>
<tr>
<td valign="top">

HashRowsPartitioned

</td>
<td valign="top">

The number of rows written to hash work tables.

</td>
</tr>
<tr>
<td valign="top">

HasSecuredFeature

</td>
<td valign="top">

Whether at least one feature of the feature set is secured \(Yes\) or not \(No\). This property has extensions that you can specify when querying the property value.

</td>
</tr>
<tr>
<td valign="top">

HashWorkTables

</td>
<td valign="top">

The number of work tables created for hash-based operations.

</td>
</tr>
<tr>
<td valign="top">

HeapsCarver

</td>
<td valign="top">

The number of heaps used for short-term purposes such as query optimization.

</td>
</tr>
<tr>
<td valign="top">

HeapsLocked

</td>
<td valign="top">

The number of relocatable heaps currently locked in the cache.

</td>
</tr>
<tr>
<td valign="top">

HeapsQuery

</td>
<td valign="top">

The number of heaps used for query processing \(hash and sort operations\).

</td>
</tr>
<tr>
<td valign="top">

HeapsRelocatable

</td>
<td valign="top">

The number of relocatable heaps.

</td>
</tr>
<tr>
<td valign="top">

http\_connection\_pool\_basesize

</td>
<td valign="top">

The nominal threshold size of database connections. This property corresponds to the http\_connection\_pool\_basesize option.

</td>
</tr>
<tr>
<td valign="top">

http\_connection\_pool\_timeout

</td>
<td valign="top">

The maximum length of time that unused connections are stored in the connection pool. This property corresponds to the http\_connection\_pool\_timeout option.

</td>
</tr>
<tr>
<td valign="top">

http\_session\_timeout

</td>
<td valign="top">

The current HTTP session timeout, in minutes. This property corresponds to http\_session\_timeout option.

</td>
</tr>
<tr>
<td valign="top">

HttpServiceName

</td>
<td valign="top">

The service name entry point for the current HTTP request. This property is useful for error reporting and flow control. An empty string is returned when this property is selected from a stored procedure that did not originate from an HTTP request or if the connection is currently inactive or waiting to continue an HTTP session.

</td>
</tr>
<tr>
<td valign="top">

IdleTimeout

</td>
<td valign="top">

The idle timeout value of the connection. The value is *NA* if the request that is currently executing is part of an event handler.

</td>
</tr>
<tr>
<td valign="top">

IndAdd

</td>
<td valign="top">

The number of entries that have been added to indexes.

</td>
</tr>
<tr>
<td valign="top">

IndLookup

</td>
<td valign="top">

The number of entries that have been looked up in indexes.

</td>
</tr>
<tr>
<td valign="top">

isolation\_level

</td>
<td valign="top">

The isolation level of the connection. This property corresponds to the isolation\_level option.

</td>
</tr>
<tr>
<td valign="top">

java\_class\_path

</td>
<td valign="top">

The list of additional directories or JAR files that are searched for classes. This property corresponds to the java\_class\_path option.

</td>
</tr>
<tr>
<td valign="top">

java\_location

</td>
<td valign="top">

The path of the Java VM for the database if one has been specified. This property corresponds to the java\_location option.

</td>
</tr>
<tr>
<td valign="top">

java\_vm\_options

</td>
<td valign="top">

The command line options that the database server uses when it launches the Java VM. This property corresponds to the java\_vm\_options option.

</td>
</tr>
<tr>
<td valign="top">

java\_main\_userid

</td>
<td valign="top">

This property is deprecated.

</td>
</tr>
<tr>
<td valign="top">

Language

</td>
<td valign="top">

The locale language.

</td>
</tr>
<tr>
<td valign="top">

LastCommitRedoPos

</td>
<td valign="top">

The redo log position after the last COMMIT operation was written to the transaction log by the connection.

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

LastPlanText

</td>
<td valign="top">

The long text plan of the last query executed on the connection. You control the remembering of the last plan by setting the RememberLastPlan option of the sa\_server\_option system procedure, or using the -zp server option.

</td>
</tr>
<tr>
<td valign="top">

LastReqTime

</td>
<td valign="top">

The time at which the last request for the specified connection started, in the timezone of the database. This property can return an empty string for internal connections, such as events. If the database has the time\_zone option set, then the value is returned using the database's time zone.

</td>
</tr>
<tr>
<td valign="top">

LastStatement

</td>
<td valign="top">

The most recently prepared SQL statement for the current connection. The LastStatement value is set when a statement is prepared, and is cleared when a statement is dropped. Only one statement string is remembered for each connection. When client statement caching is enabled and a cached statement is reused, the value is an empty string. If sa\_conn\_activity reports a non-empty value for a connection, it is most likely the statement that the connection is currently executing. If the statement had completed, it would likely have been dropped and the property value would have been cleared. If an application prepares multiple statements and retains their statement handles, then the LastStatement value does not reflect what a connection is currently doing.

</td>
</tr>
<tr>
<td valign="top">

LivenessTimeout

</td>
<td valign="top">

The liveness timeout period for the current connection. The value is *NA* if the request that is currently executing is part of an event handler.

</td>
</tr>
<tr>
<td valign="top">

lock\_rejected\_rows

</td>
<td valign="top">

This property is reserved for system use. Do not change the setting of this option.

</td>
</tr>
<tr>
<td valign="top">

LockCount

</td>
<td valign="top">

The number of locks held by the connection.

</td>
</tr>
<tr>
<td valign="top">

LockObjectOID

</td>
<td valign="top">

The value is zero if the connection isn't blocked on a table, mutex, or a semaphore, or if the connection is on a different database than the connection calling CONNECTION\_PROPERTY. Otherwise, LockObjectOID is the object ID of the table, permanent mutex, or permanent semaphore that the connection is blocked on. A negative value indicates the ID of a temporary mutex or semaphore. LockObjectOID can be used to look up information about temporary mutexes and semaphores using the sp\_list\_mutexes\_semaphores system procedure. If the object is a table, LockObjectOID can be used to look up table information using the SYSTAB system view.

</td>
</tr>
<tr>
<td valign="top">

LockObjectType

</td>
<td valign="top">

The ID for the type of object the connection is blocked on. Use the ID to look up the object type in the SYSOBJECT view. Can be one of 'TABLE' or 'MUTEX SEMAPHORE'.

</td>
</tr>
<tr>
<td valign="top">

LockIndexID

</td>
<td valign="top">

The identifier of the locked index.

</td>
</tr>
<tr>
<td valign="top">

LockName

</td>
<td valign="top">

The 64-bit unsigned integer value representing the lock for which a connection is waiting.

</td>
</tr>
<tr>
<td valign="top">

LockRowID

</td>
<td valign="top">

The identifier of the locked row.

</td>
</tr>
<tr>
<td valign="top">

LockTableOID

</td>
<td valign="top">

Zero if the connection isn't blocked, or isn't blocked on a table, or if the connection is on a different database than the connection calling CONNECTION\_PROPERTY. Otherwise, this is the object ID of the table for the lock on which this connection is waiting. The object ID can be used to look up table information using the SYSTAB system view.

</td>
</tr>
<tr>
<td valign="top">

log\_deadlocks

</td>
<td valign="top">

Whether deadlock information is recorded \(On\) or not \(Off\). This property corresponds to the log\_deadlocks option.

</td>
</tr>
<tr>
<td valign="top">

LogFreeCommit

</td>
<td valign="top">

The number of redo free commits. A redo free commit occurs when a commit of the transaction log is requested but the log has already been written \(so the commit was done for free.\)

</td>
</tr>
<tr>
<td valign="top">

login\_mode

</td>
<td valign="top">

The type of login that is supported. This property corresponds to the login\_mode option.

</td>
</tr>
<tr>
<td valign="top">

login\_procedure

</td>
<td valign="top">

The name of the stored procedure used to set compatibility options at startup. This property corresponds to the login\_procedure option.

</td>
</tr>
<tr>
<td valign="top">

LoginTime

</td>
<td valign="top">

The date and time the connection was established. If the database has the time\_zone option set, then the value is returned using the database's time zone.

</td>
</tr>
<tr>
<td valign="top">

LogWrite

</td>
<td valign="top">

The number of pages that have been written to the transaction log.

</td>
</tr>
<tr>
<td valign="top">

materialized\_view\_optimization

</td>
<td valign="top">

The value of the materialized\_view\_optimization option for the connection, which indicates whether materialized views are used during query optimization.

</td>
</tr>
<tr>
<td valign="top">

max\_connections

</td>
<td valign="top">

The value of the max\_connections option, which indicates the number of concurrent connections allowed to the database.

</td>
</tr>
<tr>
<td valign="top">

max\_client\_statements\_cached

</td>
<td valign="top">

The value of the max\_client\_statements\_cached option, which indicates the number of statements cached by the client.

</td>
</tr>
<tr>
<td valign="top">

max\_cursor\_count

</td>
<td valign="top">

The maximum number of cursors that a connection can use at once. This property corresponds to the max\_cursor\_count option.

</td>
</tr>
<tr>
<td valign="top">

max\_hash\_size

</td>
<td valign="top">

This property is deprecated.

</td>
</tr>
<tr>
<td valign="top">

max\_plans\_cached

</td>
<td valign="top">

The maximum number of execution plans to be stored in a cache. This property corresponds to the max\_plans\_cached option.

</td>
</tr>
<tr>
<td valign="top">

max\_priority

</td>
<td valign="top">

The maximum priority level a connection can have. This property corresponds to the max\_priority option for the connection.

</td>
</tr>
<tr>
<td valign="top">

max\_query\_tasks

</td>
<td valign="top">

The maximum number of requests that the database server can use to process a query. This property corresponds to the max\_query\_tasks option.

</td>
</tr>
<tr>
<td valign="top">

max\_recursive\_iterations

</td>
<td valign="top">

The maximum number of iterations a recursive common table expression can make. This property corresponds to the max\_recursive\_iterations option.

</td>
</tr>
<tr>
<td valign="top">

max\_statement\_count

</td>
<td valign="top">

The maximum number of prepared statements that a connection can use simultaneously. This property corresponds to max\_statement\_count option.

</td>
</tr>
<tr>
<td valign="top">

max\_temp\_space

</td>
<td valign="top">

The maximum amount of temporary file space available for a connection. This property corresponds to the max\_temp\_space option for the connection.

</td>
</tr>
<tr>
<td valign="top">

MessageReceived

</td>
<td valign="top">

The string that was generated by the MESSAGE statement that caused the WAITFOR statement to be interrupted. Otherwise, an empty string is returned.

</td>
</tr>
<tr>
<td valign="top">

min\_password\_length

</td>
<td valign="top">

The minimum length for new passwords in the database. This property corresponds to min\_password\_length option.

</td>
</tr>
<tr>
<td valign="top">

min\_role\_admins

</td>
<td valign="top">

The minimum number of administrators required for a role. This property corresponds to the min\_role\_admins option.

</td>
</tr>
<tr>
<td valign="top">

min\_tls\_version

</td>
<td valign="top">

The minimum downgrade version for TLS encryption.

</td>
</tr>
<tr>
<td valign="top">

Name

</td>
<td valign="top">

The name of the current connection. You can specify a connection name using the ConnectionName \(CON\) connection parameter.

</td>
</tr>
<tr>
<td valign="top">

NcharCharSet

</td>
<td valign="top">

The NCHAR character set used by the connection. This property has extensions that you can specify when querying the property value.

</td>
</tr>
<tr>
<td valign="top">

nearest\_century

</td>
<td valign="top">

The value of the nearest\_century option, which indicates how two-digit years are interpreted in string-to-date conversions.

</td>
</tr>
<tr>
<td valign="top">

NodeAddress

</td>
<td valign="top">

The node for the client in a client/server connection. When the client and server are both on the same computer, an empty string is returned.

</td>
</tr>
<tr>
<td valign="top">

non\_keywords

</td>
<td valign="top">

The value of the non\_keywords option, which is a list of keywords, if any, that are turned off so they can be used as identifiers.

</td>
</tr>
<tr>
<td valign="top">

NumLocalTempTables

</td>
<td valign="top">

The number of local temporary tables in use by the connection.

</td>
</tr>
<tr>
<td valign="top">

Number

</td>
<td valign="top">

The connection ID \(a number\) for the current connection.

</td>
</tr>
<tr>
<td valign="top">

odbc\_describe\_binary\_as\_varbinary

</td>
<td valign="top">

The value is Off if the data lake Relational Engine ODBC driver describes both BINARY and VARBINARY columns as SQL\_BINARY. The value is On if the ODBC driver describes BINARY and VARBINARY columns as SQL\_VARBINARY. This property corresponds to the odbc\_describe\_binary\_as\_varbinary option.

</td>
</tr>
<tr>
<td valign="top">

odbc\_distinguish\_char\_and\_varchar

</td>
<td valign="top">

Whether CHAR columns are described as SQL\_CHAR \(On\) or they are described as SQL\_VARCHAR \(OFF\). This property corresponds to the odbc\_distinguish\_char\_and\_varchar option.

</td>
</tr>
<tr>
<td valign="top">

oem\_string

</td>
<td valign="top">

The string stored in the header page of the database file. This property corresponds to the oem\_string option.

</td>
</tr>
<tr>
<td valign="top">

on\_charset\_conversion\_failure

</td>
<td valign="top">

The behavior when an error is encountered during character set conversion. This property corresponds to the on\_charset\_conversion\_failure option.

</td>
</tr>
<tr>
<td valign="top">

on\_tsql\_error

</td>
<td valign="top">

The behavior when an error is encountered while executing a stored procedure or T-SQL batch. This property corresponds to the on\_tsql\_error option.

</td>
</tr>
<tr>
<td valign="top">

optimization\_goal

</td>
<td valign="top">

How query processing is optimized. This property corresponds to the optimization\_goal option.

</td>
</tr>
<tr>
<td valign="top">

optimization\_level

</td>
<td valign="top">

The value of the optimization\_level option, which is a value between 0 and 15. This number is used to control the level of effort made by the data lake Relational Engine query optimizer to find an access plan for a SQL statement.

</td>
</tr>
<tr>
<td valign="top">

optimization\_workload

</td>
<td valign="top">

The level of effort made by the data lake Relational Engine query optimizer to find an access plan for a SQL statement. This property corresponds to the optimization\_workload option for the connection.t

</td>
</tr>
<tr>
<td valign="top">

OSUser

</td>
<td valign="top">

The operating system user name associated with the client process. If the client process is impersonating another user \(or the set ID bit is set\), the impersonated user name is returned. An empty string is returned for version 10.0.1 and earlier clients, and for HTTP and TDS clients.

</td>
</tr>
<tr>
<td valign="top">

PacketSize

</td>
<td valign="top">

The packet size used by the connection, in bytes. The value is *NA* if the request that is currently executing is part of an event handler. This property corresponds to the CommBufferSize \(CBSIZE\) connection parameter.

</td>
</tr>
<tr>
<td valign="top">

PacketsReceived

</td>
<td valign="top">

The number of client/server communication packets received. This value is not updated for HTTP or HTTPS connections.

</td>
</tr>
<tr>
<td valign="top">

PacketsReceivedUncomp

</td>
<td valign="top">

The number of packets that would have been received during client/server communications if compression was disabled. \(This value is the same as the value for PacketsReceived if compression is disabled.\)

</td>
</tr>
<tr>
<td valign="top">

PacketsSent

</td>
<td valign="top">

The number of client/server communication packets sent. This value is not updated for HTTP or HTTPS connections.

</td>
</tr>
<tr>
<td valign="top">

PacketsSentUncomp

</td>
<td valign="top">

The number of packets that would have been sent during client/server communications if compression was disabled. \(This value is the same as the value for PacketsSent if compression is disabled.\)

</td>
</tr>
<tr>
<td valign="top">

parameterization\_level

</td>
<td valign="top">

The value of the parameterization\_level option for the connection, which indicates the statement parameterization behavior.

</td>
</tr>
<tr>
<td valign="top">

ParameterizationPrepareCount

</td>
<td valign="top">

The number of prepares for statements that have been automatically parameterized.

</td>
</tr>
<tr>
<td valign="top">

ParentConnection

</td>
<td valign="top">

The connection ID of the connection that created a temporary connection to perform a database operation \(such as performing a backup or creating a database\). For other types of connections, the value is NULL.

</td>
</tr>
<tr>
<td valign="top">

pinned\_cursor\_percent\_of\_cache

</td>
<td valign="top">

The value of the pinned\_cursor\_percent\_of\_cache option, which indicates the percentage of the cache that can be used for pinning cursors.

</td>
</tr>
<tr>
<td valign="top">

post\_login\_procedure

</td>
<td valign="top">

The name of the procedure whose result set contains messages that should be displayed by applications when a user connects. This property corresponds to the post\_login\_procedure option.

</td>
</tr>
<tr>
<td valign="top">

precision

</td>
<td valign="top">

The value of the precision option, which indicates the decimal and numeric precision setting.

</td>
</tr>
<tr>
<td valign="top">

prefetch

</td>
<td valign="top">

The value of the prefetch option. The value is Off if no prefetching is done. The value is Conditional if prefetching occurs unless the cursor type is SENSITIVE or the query includes a proxy table. The value is Always if prefetching is done even for SENSITIVE cursor types and cursors that involve a proxy table.

</td>
</tr>
<tr>
<td valign="top">

Prepares

</td>
<td valign="top">

The number of statement preparations performed for the connection.

</td>
</tr>
<tr>
<td valign="top">

PrepStmt

</td>
<td valign="top">

The number of prepared statements currently being maintained by the database server for this connection.

</td>
</tr>
<tr>
<td valign="top">

preserve\_source\_format

</td>
<td valign="top">

Whether the original source definition of procedures, triggers, views, and event handlers is saved in system tables \(On\) or not \(Off\). This property corresponds to the preserve\_source\_format option.

</td>
</tr>
<tr>
<td valign="top">

prevent\_article\_pkey\_update

</td>
<td valign="top">

Whether updates are not allowed to the primary key columns of tables involved in publications \(On\) or not \(Off\). This property corresponds to the prevent\_article\_pkey\_update option.

</td>
</tr>
<tr>
<td valign="top">

priority

</td>
<td valign="top">

The value of the priority option for the connection, which indicates the priority level of a connection.

</td>
</tr>
<tr>
<td valign="top">

Progress

</td>
<td valign="top">

Information about how long a query has been running. This property has extensions that you can specify when querying the property value.

</td>
</tr>
<tr>
<td valign="top">

progress\_messages

</td>
<td valign="top">

The value of the progress\_messages option.

</td>
</tr>
<tr>
<td valign="top">

query\_mem\_timeout

</td>
<td valign="top">

The value of the query\_mem\_timeout option.

</td>
</tr>
<tr>
<td valign="top">

QueryBypassed

</td>
<td valign="top">

The number of requests optimized by the optimizer bypass.

</td>
</tr>
<tr>
<td valign="top">

QueryBypassedCosted

</td>
<td valign="top">

The number of requests processed by the optimizer bypass using costing.

</td>
</tr>
<tr>
<td valign="top">

QueryBypassedHeuristic

</td>
<td valign="top">

The number of requests processed by the optimizer bypass using heuristics.

</td>
</tr>
<tr>
<td valign="top">

QueryBypassedOptimized

</td>
<td valign="top">

The number of requests initially processed by the optimizer bypass and subsequently fully optimized by the optimizer.

</td>
</tr>
<tr>
<td valign="top">

QueryCachedPlans

</td>
<td valign="top">

The number of query execution plans currently cached for the connection.

</td>
</tr>
<tr>
<td valign="top">

QueryCachePages

</td>
<td valign="top">

The number of cache pages used to cache execution plans.

</td>
</tr>
<tr>
<td valign="top">

QueryDescribedBypass

</td>
<td valign="top">

The number of describe requests processed by the optimizer bypass.

</td>
</tr>
<tr>
<td valign="top">

QueryDescribedOptimizer

</td>
<td valign="top">

The number of describe requests processed by the optimizer.

</td>
</tr>
<tr>
<td valign="top">

QueryHeapPages

</td>
<td valign="top">

The number of cache pages used for query processing \(hash and sort operations\).

</td>
</tr>
<tr>
<td valign="top">

QueryJHToJNLOptUsed

</td>
<td valign="top">

The number of times a hash join was converted to a nested loop join.

</td>
</tr>
<tr>
<td valign="top">

QueryLowMemoryStrategy

</td>
<td valign="top">

The number of times the server changed its execution plan during execution as a result of low memory conditions. The strategy can change because less memory is currently available than the optimizer estimated, or because the execution plan required more memory than the optimizer estimated.

</td>
</tr>
<tr>
<td valign="top">

QueryMemActiveCurr

</td>
<td valign="top">

The number of requests actively using query memory.

</td>
</tr>
<tr>
<td valign="top">

QueryMemGrantFailed

</td>
<td valign="top">

The total number of times a request waited for query memory, but failed to get it.

</td>
</tr>
<tr>
<td valign="top">

QueryMemGrantGranted

</td>
<td valign="top">

The number of pages currently granted to requests.

</td>
</tr>
<tr>
<td valign="top">

QueryMemGrantRequested

</td>
<td valign="top">

The total number of times any request attempted to acquire query memory.

</td>
</tr>
<tr>
<td valign="top">

QueryMemGrantWaited

</td>
<td valign="top">

The total number of times any request waited for query memory.

</td>
</tr>
<tr>
<td valign="top">

QueryMemGrantWaiting

</td>
<td valign="top">

The current number of requests waiting for query memory.

</td>
</tr>
<tr>
<td valign="top">

QueryOpened

</td>
<td valign="top">

The number of OPEN requests for execution.

</td>
</tr>
<tr>
<td valign="top">

QueryOptimized

</td>
<td valign="top">

The number of requests fully optimized.

</td>
</tr>
<tr>
<td valign="top">

QueryReused

</td>
<td valign="top">

The number of requests that have been reused from the plan cache.

</td>
</tr>
<tr>
<td valign="top">

QueryRowsFetched

</td>
<td valign="top">

The number of rows that have been read from base tables, either by a sequential scan or an index scan, for this connection.

</td>
</tr>
<tr>
<td valign="top">

QueryRowsMaterialized

</td>
<td valign="top">

The number of rows that are written to work tables during query processing.

</td>
</tr>
<tr>
<td valign="top">

quoted\_identifier

</td>
<td valign="top">

Whether strings enclosed in double quotes are interpreted as identifiers \(On\), or if they are interpreted as literal strings \(Off\). This property corresponds to the quoted\_identifier option.

</td>
</tr>
<tr>
<td valign="top">

read\_past\_deleted

</td>
<td valign="top">

Whether sequential scans at isolation levels 1 and 2 skip uncommitted deleted rows \(On\), or sequential scans block on uncommitted deleted rows at isolation levels 1 and 2 \(Off\). This property corresponds to the read\_past\_deleted option.

</td>
</tr>
<tr>
<td valign="top">

recovery\_time

</td>
<td valign="top">

The maximum length of time, in minutes, that the database server will take to recover from system failure. This property corresponds to the recovery\_time option.

</td>
</tr>
<tr>
<td valign="top">

RecursiveIterations

</td>
<td valign="top">

The number of iterations for recursive unions.

</td>
</tr>
<tr>
<td valign="top">

RecursiveIterationsHash

</td>
<td valign="top">

The number of times recursive hash join used a hash strategy.

</td>
</tr>
<tr>
<td valign="top">

RecursiveIterationsNested

</td>
<td valign="top">

The number of times recursive hash join used a nested loop strategy.

</td>
</tr>
<tr>
<td valign="top">

RecursiveJNLMisses

</td>
<td valign="top">

The number of index probe cache misses for recursive hash join.

</td>
</tr>
<tr>
<td valign="top">

RecursiveJNLProbes

</td>
<td valign="top">

The number of times recursive hash join attempted an index probe.

</td>
</tr>
<tr>
<td valign="top">

remote\_idle\_timeout

</td>
<td valign="top">

The time, in seconds, of inactivity that web service client procedures and functions will tolerate. This property corresponds to the remote\_idle\_timeout option.

</td>
</tr>
<tr>
<td valign="top">

replicate\_all

</td>
<td valign="top">

For internal use only.

</td>
</tr>
<tr>
<td valign="top">

ReqCountActive

</td>
<td valign="top">

The number of requests processed, or NULL if the RequestTiming server property is set to Off.

</td>
</tr>
<tr>
<td valign="top">

ReqCountBlockContention

</td>
<td valign="top">

The number of times the connection waited for atomic access, or NULL if the -zt option was not specified.

</td>
</tr>
<tr>
<td valign="top">

ReqCountBlockIO

</td>
<td valign="top">

The number of times the connection waited for I/O to complete, or NULL if the -zt option was not specified.

</td>
</tr>
<tr>
<td valign="top">

ReqCountBlockLock

</td>
<td valign="top">

The number of times the connection waited for a lock, or NULL if the -zt option was not specified.

</td>
</tr>
<tr>
<td valign="top">

ReqCountUnscheduled

</td>
<td valign="top">

The number of times the connection waited for scheduling, or NULL if the -zt option was not specified.

</td>
</tr>
<tr>
<td valign="top">

ReqStatus

</td>
<td valign="top">

The status of the request. The value is Idle when the connection is not currently processing a request. The value is Unscheduled\* when the connection has work to do and is waiting for an available database server worker. The value is BlockedIO\* when the connection is blocked waiting for an I/O. The value is BlockedContention\* when the connection is blocked waiting for access to shared database server data structures. The value is BlockedLock when the connection is blocked waiting for a locked object. The value is Executing when the connection is executing a request. The values marked with an asterisk \(\*\) are only returned when logging of request timing information has been turned on for the database server using the -zt server option. If request timing information is not being logged \(the default\), the values are reported as Executing.

</td>
</tr>
<tr>
<td valign="top">

ReqTimeActive

</td>
<td valign="top">

The amount of time in seconds spent processing requests, or NULL if the -zt option was not specified.

</td>
</tr>
<tr>
<td valign="top">

ReqTimeBlockContention

</td>
<td valign="top">

The amount of time in seconds spent waiting for atomic access, or NULL if the RequestTiming server property is set to Off.

</td>
</tr>
<tr>
<td valign="top">

ReqTimeBlockIO

</td>
<td valign="top">

The amount of time in seconds spent waiting for I/O to complete, or NULL if the -zt option was not specified.

</td>
</tr>
<tr>
<td valign="top">

ReqTimeBlockLock

</td>
<td valign="top">

The amount of time in seconds spent waiting for a lock, or NULL if the -zt option was not specified.

</td>
</tr>
<tr>
<td valign="top">

ReqTimeUnscheduled

</td>
<td valign="top">

The amount of unscheduled time in seconds, or NULL if the -zt option was not specified.

</td>
</tr>
<tr>
<td valign="top">

ReqType

</td>
<td valign="top">

The type of the last request. If a connection has been cached by connection pooling, its ReqType value is CONNECT\_POOL\_CACHE.

</td>
</tr>
<tr>
<td valign="top">

request\_timeout

</td>
<td valign="top">

The value of the request\_timeout option, which indicates the maximum time a single request can run.

</td>
</tr>
<tr>
<td valign="top">

RequestsReceived

</td>
<td valign="top">

The number of client/server communication requests or round trips. It is different from PacketsReceived in that multi-packet requests count as one request, and liveness packets are not included.

</td>
</tr>
<tr>
<td valign="top">

reserved\_connections

</td>
<td valign="top">

The number of connections that are reserved for standard connections. This property corresponds to the reserved\_connections option.

</td>
</tr>
<tr>
<td valign="top">

reserved\_keywords

</td>
<td valign="top">

The value of the reserved\_keywords option, which specifies a list of non-default reserved keywords that are enabled for the database.

</td>
</tr>
<tr>
<td valign="top">

return\_date\_time\_as\_string

</td>
<td valign="top">

Whether DATE, TIME, and TIMESTAMP values are returned to applications as a string \(On\), or they are returned as a DATE, TIME, or TIMESTAMP data type \(Off\). This property corresponds to the return\_date\_time\_as\_string option.

</td>
</tr>
<tr>
<td valign="top">

Rlbk

</td>
<td valign="top">

The number of rollback requests that have been handled.

</td>
</tr>
<tr>
<td valign="top">

rollback\_on\_deadlock

</td>
<td valign="top">

Whether transaction are automatically rolled back if it encounters a deadlock \(On\) or not \(Off\). This property corresponds to the rollback\_on\_deadlock option.

</td>
</tr>
<tr>
<td valign="top">

RollbackLogPages

</td>
<td valign="top">

The number of pages in the rollback log.

</td>
</tr>
<tr>
<td valign="top">

row\_counts

</td>
<td valign="top">

Whether the row count is always accurate \(On\), or the row count is usually an estimate \(Off\). This property corresponds to the row\_counts option.

</td>
</tr>
<tr>
<td valign="top">

scale

</td>
<td valign="top">

The decimal and numeric scale for the connection. This property corresponds to the scale option.

</td>
</tr>
<tr>
<td valign="top">

secure\_feature\_key

</td>
<td valign="top">

This property is deprecated. The value of the secure\_feature\_key option, which stores the key that is used to enable and disable features for a database server. Selecting the value of this property always returns an empty string.

</td>
</tr>
<tr>
<td valign="top">

ServerNodeAddress

</td>
<td valign="top">

The node for the server in a client/server connection. When the client and server are both on the same computer, an empty string is returned. The value is *NA* if the request that is currently executing is part of an event handler.

</td>
</tr>
<tr>
<td valign="top">

ServerPort

</td>
<td valign="top">

The database server's TCP/IP port number or 0.

</td>
</tr>
<tr>
<td valign="top">

SessionCreateTime

</td>
<td valign="top">

The time the HTTP session was created. If the database has the time\_zone option set, then the value is returned using the database's time zone.

</td>
</tr>
<tr>
<td valign="top">

SessionID

</td>
<td valign="top">

The session ID for the connection if it exists, otherwise, an empty string.

</td>
</tr>
<tr>
<td valign="top">

SessionLastTime

</td>
<td valign="top">

The time of the last request for the HTTP session. If the database has the time\_zone option set, then the value is returned using the database's time zone.

</td>
</tr>
<tr>
<td valign="top">

SessionTimeout

</td>
<td valign="top">

The time, in minutes, the HTTP session persists during inactivity.

</td>
</tr>
<tr>
<td valign="top">

SnapshotCount

</td>
<td valign="top">

The number of snapshots associated with the connection.

</td>
</tr>
<tr>
<td valign="top">

sort\_collation

</td>
<td valign="top">

The value of the sort\_collation option. The value is Internal if the ORDER BY clause remains unchanged; otherwise, the value is the collation name or the collation ID.

</td>
</tr>
<tr>
<td valign="top">

SortMergePasses

</td>
<td valign="top">

The number of merge passes used during sorting.

</td>
</tr>
<tr>
<td valign="top">

SortRowsMaterialized

</td>
<td valign="top">

The number of rows written to sort work tables.

</td>
</tr>
<tr>
<td valign="top">

SortRunsWritten

</td>
<td valign="top">

The number of sorted runs written during sorting.

</td>
</tr>
<tr>
<td valign="top">

SortSortedRuns

</td>
<td valign="top">

The number of sorted runs created during run formation.

</td>
</tr>
<tr>
<td valign="top">

SortWorkTables

</td>
<td valign="top">

The number of work tables created for sorting.

</td>
</tr>
<tr>
<td valign="top">

sql\_flagger\_error\_level

</td>
<td valign="top">

The value of the sql\_flagger\_error\_level option, which controls the response to any SQL that is not part of the specified standard. This property corresponds to the sql\_flagger\_error\_level option.

</td>
</tr>
<tr>
<td valign="top">

sql\_flagger\_warning\_level

</td>
<td valign="top">

The value of the sql\_flagger\_warning\_level. This property corresponds to the sql\_flagger\_warning\_level option.

</td>
</tr>
<tr>
<td valign="top">

st\_geometry\_asbinary\_format

</td>
<td valign="top">

How spatial values are converted from a geometry to a binary format. This property corresponds to the st\_geometry\_asbinary\_format option.

</td>
</tr>
<tr>
<td valign="top">

st\_geometry\_astext\_format

</td>
<td valign="top">

How spatial values are converted from a geometry to text. This property corresponds to the st\_geometry\_astext\_format option.

</td>
</tr>
<tr>
<td valign="top">

st\_geometry\_asxml\_format

</td>
<td valign="top">

How spatial values are converted from a geometry to XML. This property corresponds to the st\_geometry\_asxml\_format option.

</td>
</tr>
<tr>
<td valign="top">

st\_geometry\_describe\_type

</td>
<td valign="top">

How spatial values are described. This property corresponds to the st\_geometry\_describe\_type option.

</td>
</tr>
<tr>
<td valign="top">

st\_geometry\_interpolation

</td>
<td valign="top">

The interpolation setting for ST\_CircularString geometries. This property corresponds to st\_geometry\_interpolation option.

</td>
</tr>
<tr>
<td valign="top">

st\_geometry\_on\_invalid

</td>
<td valign="top">

The behavior when a geometry fails surface validation. This property corresponds to the st\_geometry\_on\_invalid option.

</td>
</tr>
<tr>
<td valign="top">

StatementDescribes

</td>
<td valign="top">

The total number of statements processed by DESCRIBE requests.

</td>
</tr>
<tr>
<td valign="top">

StatementPostAnnotates

</td>
<td valign="top">

The number of statements processed by the semantic query transformation phase.

</td>
</tr>
<tr>
<td valign="top">

StatementPostAnnotatesSimple

</td>
<td valign="top">

The number of statements processed by the semantic query transformation phase, but that skipped some of the semantic transformations.

</td>
</tr>
<tr>
<td valign="top">

StatementPostAnnotatesSkipped

</td>
<td valign="top">

The number of statements that have completely skipped the semantic query transformation phase.

</td>
</tr>
<tr>
<td valign="top">

string\_rtruncation

</td>
<td valign="top">

Whether an error is raised when a string is truncated \(On\), or no error is not raised \(Off\) This property corresponds to the string\_rtruncation option.

</td>
</tr>
<tr>
<td valign="top">

subsume\_row\_locks

</td>
<td valign="top">

Whether the database server acquires individual row locks for a table \(On\), or not \(Off\). This property corresponds to the subsume\_row\_locks option.

</td>
</tr>
<tr>
<td valign="top">

suppress\_tds\_debugging

</td>
<td valign="top">

Whether TDS debugging information appears in the database server messages window \(Off\), or the debugging information does not appear in the database server messages window \(On\). This property corresponds to the suppress\_tds\_debugging option.

</td>
</tr>
<tr>
<td valign="top">

synchronize\_mirror\_on\_commit

</td>
<td valign="top">

Whether the database mirror server is synchronized on commit \(On\) or not \(Off\). This property corresponds to the synchronize\_mirror\_on\_commit option.

</td>
</tr>
<tr>
<td valign="top">

tds\_empty\_string\_is\_null

</td>
<td valign="top">

Whether empty strings are returned as NULL for TDS connections \(On\), or if a string containing one blank character is returned for TDS connections \(Off\). This property corresponds to the tds\_empty\_string\_is\_null option.

</td>
</tr>
<tr>
<td valign="top">

temp\_space\_limit\_check

</td>
<td valign="top">

Whether the database server checks the amount of temporary space available for a connection \(On\), or the database server does not check the amount of space available for a connection \(Off\). This property corresponds to the temp\_space\_limit\_check option.

</td>
</tr>
<tr>
<td valign="top">

TempFilePages

</td>
<td valign="top">

The number of temporary file pages used by the connection.

</td>
</tr>
<tr>
<td valign="top">

TempTablePages

</td>
<td valign="top">

The number of pages in the temporary file used for temporary tables.

</td>
</tr>
<tr>
<td valign="top">

time\_format

</td>
<td valign="top">

The string format used for times retrieved from the database. This property corresponds to the time\_format option.

</td>
</tr>
<tr>
<td valign="top">

time\_zone

</td>
<td valign="top">

The time zone that the database uses for time zone calculations. This property corresponds to the time\_zone option.

</td>
</tr>
<tr>
<td valign="top">

time\_zone\_adjustment

</td>
<td valign="top">

The number of minutes that must be added to the Coordinated Universal Time \(UTC\) to display time local to the connection. This property corresponds to the time\_zone\_adjustment option.

</td>
</tr>
<tr>
<td valign="top">

timestamp\_format

</td>
<td valign="top">

The format for timestamps that are retrieved from the database. This property corresponds to the timestamp\_format option.

</td>
</tr>
<tr>
<td valign="top">

timestamp\_with\_time\_zone\_format

</td>
<td valign="top">

The format for TIMESTAMP WITH TIME ZONE values retrieved from the database. This property corresponds to the timestamp\_with\_time\_zone\_format option.

</td>
</tr>
<tr>
<td valign="top">

TimeZoneAdjustment

</td>
<td valign="top">

The number of minutes that must be added to the Coordinated Universal Time \(UTC\) to display time local to the connection.

</td>
</tr>
<tr>
<td valign="top">

TLSCipher

</td>
<td valign="top">

The cipher used to secure the current connection. Displays 'None' if not a secure connection.

</td>
</tr>
<tr>
<td valign="top">

TLSSuites

</td>
<td valign="top">

A colon-separated list of TLS cipher suites offered by the server for the current connection. Displays 'None' if not a secure connection. For the list of supported cipher suites see [TLS Support](https://help.sap.com/viewer/a89a0a8384f21015b1e7adbeca456f73/2024_1_QRC/en-US/3bcc73636c5f1014842cdeb27af3fed0.html "Transport Layer Security (TLS) encryption versions 1.2 and 1.3 are supported.") :arrow_upper_right:.

</td>
</tr>
<tr>
<td valign="top">

TLSVersion

</td>
<td valign="top">

The TLS protocol version used to secure the current connection. Displays 'None' if not a secure connection.

</td>
</tr>
<tr>
<td valign="top">

TransactionStartTime

</td>
<td valign="top">

The value is a string containing the time the database was first modified after a COMMIT or ROLLBACK, or an empty string if no modifications have been made to the database since the last COMMIT or ROLLBACK. If the database has the time\_zone option set, then the value is returned using the database's time zone.

</td>
</tr>
<tr>
<td valign="top">

truncate\_timestamp\_values

</td>
<td valign="top">

Whether the number of decimal places used in the TIMESTAMP values is limited \(On\) or not \(Off\). This property corresponds to the truncate\_timestamp\_values option.

</td>
</tr>
<tr>
<td valign="top">

tsql\_outer\_joins

</td>
<td valign="top">

Whether Transact-SQL outer joins can be used in DML statement \(On\) or not \(Off\). This property corresponds to the value of the tsql\_outer\_joins option.

</td>
</tr>
<tr>
<td valign="top">

tsql\_variables

</td>
<td valign="top">

Whether you can use the @ sign instead of the colon as a prefix for host variable names in Embedded SQL \(On\) or not \(Off\). This property corresponds to the value of the tsql\_variables option.

</td>
</tr>
<tr>
<td valign="top">

UncommitOp

</td>
<td valign="top">

The number of uncommitted operations.

</td>
</tr>
<tr>
<td valign="top">

updatable\_statement\_isolation

</td>
<td valign="top">

The isolation level \(0, 1, 2, or 3\) used by updatable statements when the isolation\_level option is set to Readonly-statement-snapshot. This property corresponds to the updatable\_statement\_isolation option.

</td>
</tr>
<tr>
<td valign="top">

update\_statistics

</td>
<td valign="top">

Whether the connection can send query feedback to the statistics governor \(On\) or the statistics governor does not receive query feedback from the current connection \(Off\). This property corresponds to the update\_statistics option.

</td>
</tr>
<tr>
<td valign="top">

upgrade\_database\_capability

</td>
<td valign="top">

This property is reserved for system use. Do not change the setting of this option.

</td>
</tr>
<tr>
<td valign="top">

user\_estimates

</td>
<td valign="top">

The value that controls whether selectivity estimates in query predicates are respected or ignored by the query optimizer. This property corresponds to the user\_estimates option.:

</td>
</tr>
<tr>
<td valign="top">

UserAppInfo

</td>
<td valign="top">

The string specified by the AppInfo connection parameter in a connection string.

</td>
</tr>
<tr>
<td valign="top">

UserDefinedCounterRate01

</td>
<td valign="top">

The current value of the user-defined performance counter. The semantics of this property are defined by the client application.

</td>
</tr>
<tr>
<td valign="top">

UserDefinedCounterRate02

</td>
<td valign="top">

The current value of the user-defined performance counter. The semantics of this property are defined by the client application.

</td>
</tr>
<tr>
<td valign="top">

UserDefinedCounterRate03

</td>
<td valign="top">

The current value of the user-defined performance counter. The semantics of this property are defined by the client application.

</td>
</tr>
<tr>
<td valign="top">

UserDefinedCounterRate04

</td>
<td valign="top">

The current value of the user-defined performance counter. The semantics of this property are defined by the client application.

</td>
</tr>
<tr>
<td valign="top">

UserDefinedCounterRate05

</td>
<td valign="top">

The current value of the user-defined performance counter. The semantics of this property are defined by the client application.

</td>
</tr>
<tr>
<td valign="top">

UserDefinedCounterRaw01

</td>
<td valign="top">

The current value of the user-defined performance counter. The semantics of this property are defined by the client application.

</td>
</tr>
<tr>
<td valign="top">

UserDefinedCounterRaw02

</td>
<td valign="top">

The current value of the user-defined performance counter. The semantics of this property are defined by the client application.

</td>
</tr>
<tr>
<td valign="top">

UserDefinedCounterRaw03

</td>
<td valign="top">

The current value of the user-defined performance counter. The semantics of this property are defined by the client application.

</td>
</tr>
<tr>
<td valign="top">

UserDefinedCounterRaw04

</td>
<td valign="top">

The current value of the user-defined performance counter. The semantics of this property are defined by the client application.

</td>
</tr>
<tr>
<td valign="top">

UserDefinedCounterRaw05

</td>
<td valign="top">

The current value of the user-defined performance counter. The semantics of this property are defined by the client application.

</td>
</tr>
<tr>
<td valign="top">

UserID

</td>
<td valign="top">

The user ID for the connection.

</td>
</tr>
<tr>
<td valign="top">

uuid\_has\_hyphens

</td>
<td valign="top">

The format of unique identifier values when they are converted to strings. When the option is set to On, the resulting strings contain four hyphens. This property corresponds to the uuid\_has\_hyphens option.

</td>
</tr>
<tr>
<td valign="top">

verify\_password\_function

</td>
<td valign="top">

The name of the function used for password verification if one has been specified. This property corresponds to the verify\_password\_function.

</td>
</tr>
<tr>
<td valign="top">

wait\_for\_commit

</td>
<td valign="top">

Whether the database does not check foreign key integrity until the next COMMIT statement \(On\), or all foreign keys that are not created with the CHECK ON COMMIT clause are checked as they are inserted, updated or deleted \(Off\). This property corresponds to the wait\_for\_commit option.

</td>
</tr>
<tr>
<td valign="top">

WaitStartTime

</td>
<td valign="top">

The time at which the connection started waiting \(or an empty string if the connection is not waiting\). If the database has the time\_zone option set, then the value is returned using the database's time zone.

</td>
</tr>
<tr>
<td valign="top">

WaitType

</td>
<td valign="top">

The reason for the wait, if it is available. The value is lock when the connection is waiting on a lock The value is waitfor when the connection is executing a WAITFOR statement. The value is an empty-string when the connection is not waiting, or when the reason for the wait is not available.

</td>
</tr>
<tr>
<td valign="top">

webservice\_namespace\_host

</td>
<td valign="top">

The hostname to be used as the XML namespace within generated WSDL documents if one has been specified. This property corresponds to the webservice\_namespace\_host option,

</td>
</tr>
<tr>
<td valign="top">

webservice\_sessionid\_name

</td>
<td valign="top">

The session identifier name that is used by the web server to determine whether session management is being used. This property corresponds to the webservice\_sessionid\_name option.

</td>
</tr>
</table>

