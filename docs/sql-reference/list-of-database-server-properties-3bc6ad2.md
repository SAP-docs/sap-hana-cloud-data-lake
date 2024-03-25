<!-- loio3bc6ad206c5f1014b043b4cc42d7fc07 -->

# List of Database Server Properties

Database server properties are available for each connection to a database. Use the PROPERTY system function to retrieve the value for an individual property and use the sa\_eng\_properties system procedure to retrieve the values of all database server properties.



## Example

The following statement returns the number of cache pages used for global server data structures:

```
SELECT PROPERTY ( 'MainHeapPages' );
```

Use the sa\_eng\_properties system procedure to retrieve the values of all database server properties:

```
CALL sa_eng_properties;
```



## Database Server Properties


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

ActiveReq

</td>
<td valign="top">

The number of server workers that are currently handling client-side requests.

</td>
</tr>
<tr>
<td valign="top">

ApproximateCPUTime

</td>
<td valign="top">

An estimate of the amount of CPU time accumulated by the database server, in seconds. The value may differ from the actual value by as much as 50 percent, although typical variations are in the 5 to 10 percent range. On multi-processor computers, each CPU \(or hyperthread or core\) accumulates time, so the sum of accumulated times for all connections may be greater than the elapsed time.

</td>
</tr>
<tr>
<td valign="top">

AutoMultiProgrammingLevel

</td>
<td valign="top">

Whether the database server is automatically adjusting its multiprogramming level.

</td>
</tr>
<tr>
<td valign="top">

AutoMultiProgrammingLevelStatistics

</td>
<td valign="top">

Whether messages about automatic adjustments to the database server's multiprogramming level are displayed in the database server message log.

</td>
</tr>
<tr>
<td valign="top">

AvailIO

</td>
<td valign="top">

The current number of available I/O control blocks.

</td>
</tr>
<tr>
<td valign="top">

BuildChange

</td>
<td valign="top">

Reserved for system use.

</td>
</tr>
<tr>
<td valign="top">

BuildClient

</td>
<td valign="top">

Reserved for system use. Do not change the setting of this property.

</td>
</tr>
<tr>
<td valign="top">

BuildProduction

</td>
<td valign="top">

Whether the database server is compiled for production use \(Yes\) or whether the database server is a debug build \(No\).

</td>
</tr>
<tr>
<td valign="top">

BuildReproducible

</td>
<td valign="top">

Reserved for system use.

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

The number of bytes that would have been received during client/server communications if compression was disabled. \(This value is the same as the value for BytesReceived if compression is disabled.\)

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

The number of bytes that would have been sent during client/server communications if compression was disabled. \(This value is the same as the value for BytesSent if compression is disabled.\)

</td>
</tr>
<tr>
<td valign="top">

CacheAllocated

</td>
<td valign="top">

The number of cache pages that have been allocated for purposes other than file caching.

</td>
</tr>
<tr>
<td valign="top">

CacheFile

</td>
<td valign="top">

The number of cache pages used to hold data from database files.

</td>
</tr>
<tr>
<td valign="top">

CacheFileDirty

</td>
<td valign="top">

The number of cache pages that are dirty \(needing a write\).

</td>
</tr>
<tr>
<td valign="top">

CacheFree

</td>
<td valign="top">

The number of cache pages not being used.

</td>
</tr>
<tr>
<td valign="top">

CacheHits

</td>
<td valign="top">

The number of database page lookups.

</td>
</tr>
<tr>
<td valign="top">

CacheMisses

</td>
<td valign="top">

The number of times a page was not in the cache.

</td>
</tr>
<tr>
<td valign="top">

CachePanics

</td>
<td valign="top">

The number of times the cache manager has failed to find a page to allocate.

</td>
</tr>
<tr>
<td valign="top">

CachePinned

</td>
<td valign="top">

The number of pinned cache pages.

</td>
</tr>
<tr>
<td valign="top">

CacheRead

</td>
<td valign="top">

The number of cache reads.

</td>
</tr>
<tr>
<td valign="top">

CacheReplacements

</td>
<td valign="top">

The number of pages in the cache that have been replaced.

</td>
</tr>
<tr>
<td valign="top">

CacheScavenges

</td>
<td valign="top">

The number of times the cache manager has scavenged for a page to allocate.

</td>
</tr>
<tr>
<td valign="top">

CacheScavengeVisited

</td>
<td valign="top">

The number of pages visited while scavenging for a page to allocate.

</td>
</tr>
<tr>
<td valign="top">

CacheSizingStatistics

</td>
<td valign="top">

Whether the database server is displaying cache sizing statistics when the cache is resized.

</td>
</tr>
<tr>
<td valign="top">

CarverHeapPages

</td>
<td valign="top">

The number of heap pages used for short-term purposes, such as query optimization.

</td>
</tr>
<tr>
<td valign="top">

CharSet

</td>
<td valign="top">

The CHAR character set in use by the database server.

</td>
</tr>
<tr>
<td valign="top">

ClientStmtCacheHits

</td>
<td valign="top">

The number of prepares that were not required because of the client statement cache. This is the number of additional prepares that would be required if client statement caching was disabled.

</td>
</tr>
<tr>
<td valign="top">

ClientStmtCacheMisses

</td>
<td valign="top">

The number of statements in the client statement cache that were prepared again. This is the number of times a cached statement was considered for reuse, but could not be reused because of a schema change, a database option setting, or a DROP VARIABLE statement.

</td>
</tr>
<tr>
<td valign="top">

CollectStatistics

</td>
<td valign="top">

Whether the database server is collecting performance statistics.

</td>
</tr>
<tr>
<td valign="top">

CommandLine

</td>
<td valign="top">

The command line arguments that were used to start the database server.

If the encryption key for a database was specified using the -ek option, the key is replaced with a constant string of asterisks in the value for this property.

If the utility database user ID and password was specified using the -su option, they are replaced with a constant string of asterisks in the value for this property.

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

CompactPlatformVer

</td>
<td valign="top">

A condensed version of the PlatformVer property.

</td>
</tr>
<tr>
<td valign="top">

CompanyName

</td>
<td valign="top">

The name of the company owning this software.

</td>
</tr>
<tr>
<td valign="top">

CompletedReq

</td>
<td valign="top">

The number of requests that have been completed.

</td>
</tr>
<tr>
<td valign="top">

ConnCount

</td>
<td valign="top">

The number of connections to the database server. This property value does not include connections used for internal operations, but does include connections used for events and external environment support.

</td>
</tr>
<tr>
<td valign="top">

ConnectedTime

</td>
<td valign="top">

The total length of time, in seconds, that all connections have been connected to the database server.

The value is updated only when a request completes for a connection or when a connection disconnects. As a result, the value can lag behind for connections that are idle or busy executing for a long time in the database server. The value includes time accrued by any connection, including database events and background server connections \(such as the database cleaner\).

</td>
</tr>
<tr>
<td valign="top">

ConnsDisabled

</td>
<td valign="top">

Whether the server option is set to disable new connections.

</td>
</tr>
<tr>
<td valign="top">

ConsoleLogFile

</td>
<td valign="top">

The name of the file where database server messages are logged if the -o option was specified. If the -option was not specified, the value is an empty string.

</td>
</tr>
<tr>
<td valign="top">

ConsoleLogMaxSize

</td>
<td valign="top">

The maximum size in bytes of the file used to log database server messages.

</td>
</tr>
<tr>
<td valign="top">

CurrentCacheSize

</td>
<td valign="top">

The current cache size, in kilobytes.

</td>
</tr>
<tr>
<td valign="top">

CurrentMirrorBackgroundWorkers

</td>
<td valign="top">

The number of workers currently being used for database mirroring background tasks. These workers are separate from those controlled by the multiprogramming level.

</td>
</tr>
<tr>
<td valign="top">

CurrentMultiProgrammingLevel

</td>
<td valign="top">

The current number of tasks that the database server can process concurrently.

</td>
</tr>
<tr>
<td valign="top">

CurrRead

</td>
<td valign="top">

The current number of file reads that were issued by the database server, but that have not completed yet.

</td>
</tr>
<tr>
<td valign="top">

CurrWrite

</td>
<td valign="top">

The current number of file writes that were issued by the database server, but that have not completed yet.

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

DebuggingInformation

</td>
<td valign="top">

Whether the server is displaying diagnostic messages for troubleshooting.

</td>
</tr>
<tr>
<td valign="top">

DefaultCollation

</td>
<td valign="top">

The collation that would be used for new databases if none is explicitly specified.

</td>
</tr>
<tr>
<td valign="top">

DefaultNcharCollation

</td>
<td valign="top">

The name of the default NCHAR collation on the server computer \(UCA if ICU is installed, and UTF8BIN otherwise\).

</td>
</tr>
<tr>
<td valign="top">

DiskRead

</td>
<td valign="top">

The number of disk reads.

</td>
</tr>
<tr>
<td valign="top">

DiskReadHintScatterLimit

</td>
<td valign="top">

The imposed limit on the size \(in bytes\) of a scatter read hint.

</td>
</tr>
<tr>
<td valign="top">

DiskRetryRead

</td>
<td valign="top">

The number of disk read retries.

</td>
</tr>
<tr>
<td valign="top">

DiskRetryReadScatter

</td>
<td valign="top">

The number of disk read retries for scattered reads.

</td>
</tr>
<tr>
<td valign="top">

DiskRetryWrite

</td>
<td valign="top">

The number of disk write retries.

</td>
</tr>
<tr>
<td valign="top">

DiskSandbox

</td>
<td valign="top">

Whether the read-write file operations of the database are restricted to the directory where the main database file is located \(On\) or not \(Off\).

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

DropBadStatistics

</td>
<td valign="top">

Automatic statistics management to drop statistics that return bad estimates.

</td>
</tr>
<tr>
<td valign="top">

DropUserStatistics

</td>
<td valign="top">

Automatic statistics management to drop statistics that have not been used for 90 consecutive days.

</td>
</tr>
<tr>
<td valign="top">

EventTypeDesc

</td>
<td valign="top">

The description of the event type associated with a given event type ID.

</td>
</tr>
<tr>
<td valign="top">

EventTypeName

</td>
<td valign="top">

The system event type name associated with a given event type ID.

</td>
</tr>
<tr>
<td valign="top">

ExchangeTasks

</td>
<td valign="top">

The number of tasks currently being used for parallel execution of queries.

</td>
</tr>
<tr>
<td valign="top">

ExchangeTasksCompleted

</td>
<td valign="top">

The total number of internal tasks that have been used for intra-query parallelism since the database server started.

</td>
</tr>
<tr>
<td valign="top">

FipsMode

</td>
<td valign="top">

Whether the -fips option was specified when the database server was started. If the -fips option was specified, all encryption and hashing use FIPS 140-2 certified algorithms.

In the Government Cloud \(US\) region, only FIPS 140-2 certified encryption modules are used, even when non-FIPS algorithms are explicitly requested.

</td>
</tr>
<tr>
<td valign="top">

FirstOption

</td>
<td valign="top">

The number that represents the first connection property that corresponds to a database option.

</td>
</tr>
<tr>
<td valign="top">

FreeBuffers

</td>
<td valign="top">

The number of available network buffers.

</td>
</tr>
<tr>
<td valign="top">

FunctionMaxParms

</td>
<td valign="top">

The maximum number of parameters that can be specified by a function. The function is identified by the value specified by the *<function-number\>*, which is a positive integer. For example:

```
SELECT PROPERTY ( 'FunctionMaxParms', <function-number> );
```

The *<function-number\>* is subject to change between releases.

</td>
</tr>
<tr>
<td valign="top">

FunctionMinParms

</td>
<td valign="top">

The minimum number of parameters that must be specified by a function. The function is identified by the value specified by the *<function-number\>*, which is a positive integer. For example:

```
SELECT PROPERTY ( 'FunctionMinParms', <function-number> );
```

The *<function-number\>* is subject to change between releases.

</td>
</tr>
<tr>
<td valign="top">

FunctionName

</td>
<td valign="top">

The name of the function identified by the value specified by the *<function-number\>* \(which is a positive integer\):

```
SELECT PROPERTY ( 'FunctionName', <function-number> );
```

The *<function-number\>* is subject to change between releases.

</td>
</tr>
<tr>
<td valign="top">

HasSecuredFeature

</td>
<td valign="top">

Whether at least one feature of the all feature set is secured at the global server level. This property has extensions that you can specify when querying the property value.

</td>
</tr>
<tr>
<td valign="top">

HasSecureFeatureKey

</td>
<td valign="top">

Whether the database server has at least one secure feature key. This property has extensions that you can specify when querying the property value.

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

HttpAddresses

</td>
<td valign="top">

A semicolon-delimited list of the IP addresses that the database server is listening to for HTTP connections from clients. For example:

```
(::1):80;127.0.0.1:80
```



</td>
</tr>
<tr>
<td valign="top">

HttpConnectionsQueued

</td>
<td valign="top">

The number of connections that are currently in the queue.

</td>
</tr>
<tr>
<td valign="top">

HttpListeners

</td>
<td valign="top">

A semicolon-delimited list of *<IP address\>*:*<port\>* pairs that the database server is using to listen for HTTP connections.

</td>
</tr>
<tr>
<td valign="top">

HttpNumActiveReq

</td>
<td valign="top">

The number of HTTP connections that are actively processing an HTTP request. An HTTP connection that has sent its response is not included.

</td>
</tr>
<tr>
<td valign="top">

HttpNumConnections

</td>
<td valign="top">

The number of HTTP connections that are currently open within the database server. They may be actively processing a request or waiting in a queue of long lived \(keep-alive\) connections.

</td>
</tr>
<tr>
<td valign="top">

HttpNumSessions

</td>
<td valign="top">

The number of active and dormant HTTP sessions within the database server.

</td>
</tr>
<tr>
<td valign="top">

HttpPorts

</td>
<td valign="top">

The HTTP port numbers for the web server as a comma-delimited list.

</td>
</tr>
<tr>
<td valign="top">

HttpQueueCount

</td>
<td valign="top">

The total number of connections that have been queued since the database server started.

</td>
</tr>
<tr>
<td valign="top">

HttpQueueMaxCount

</td>
<td valign="top">

The maximum number of connections that have been in the queue at one time.

</td>
</tr>
<tr>
<td valign="top">

HttpQueueTimedOut

</td>
<td valign="top">

The total number of connections that have timed out after sitting in the queue.

</td>
</tr>
<tr>
<td valign="top">

HttpsAddresses

</td>
<td valign="top">

A semicolon-delimited list of the IP addresses that the server is listening to for HTTPS connections from clients. For example:

```
(::1):443;127.0.0.1:443
```



</td>
</tr>
<tr>
<td valign="top">

HttpsListeners

</td>
<td valign="top">

A semicolon-delimited list of *<IP address\>*:*<port\>* pairs that the database server is using to listen for HTTPS connections.

</td>
</tr>
<tr>
<td valign="top">

HttpsNumActiveReq

</td>
<td valign="top">

The number of secure HTTPS connections that are actively processing an HTTPS request. An HTTPS connection that has sent its response is not included.

</td>
</tr>
<tr>
<td valign="top">

HttpsNumConnections

</td>
<td valign="top">

The number of HTTPS connections that are currently open within the database server. They may be actively processing a request or waiting in a queue of long lived \(keep-alive\) connections.

</td>
</tr>
<tr>
<td valign="top">

HttpsPorts

</td>
<td valign="top">

The HTTPS port numbers for the web server as a comma-delimited list.

</td>
</tr>
<tr>
<td valign="top">

IdleTimeout

</td>
<td valign="top">

The default idle timeout.

</td>
</tr>
<tr>
<td valign="top">

IPAddressMonitorPeriod

</td>
<td valign="top">

The time in seconds that a database server checks for new IP addresses.

</td>
</tr>
<tr>
<td valign="top">

IsAesniAvailable

</td>
<td valign="top">

Whether the database server computer's CPU supports the Intel AES-NI instruction set and the computer is running a supported operating system.

</td>
</tr>
<tr>
<td valign="top">

IsFipsAvailable

</td>
<td valign="top">

Whether the FIPS-certified DLL is installed.

</td>
</tr>
<tr>
<td valign="top">

IsIQ

</td>
<td valign="top">

Reserved for system use.

</td>
</tr>
<tr>
<td valign="top">

IsNetworkServer

</td>
<td valign="top">

Whether the connection is to a network database server \(Yes\), or to a personal database server \(No\).

</td>
</tr>
<tr>
<td valign="top">

IsPortableDevice

</td>
<td valign="top">

Whether the database server is running on a laptop, notebook, or other portable device.

VMware is not taken into account, so the value is No for a database server running on a VM that is running on a laptop.

This property is always NULL on Linux systems.

</td>
</tr>
<tr>
<td valign="top">

IsRsaAvailable

</td>
<td valign="top">

Whether the RSA DLL is installed.

</td>
</tr>
<tr>
<td valign="top">

IsRuntimeServer

</td>
<td valign="top">

This property is No for all versions of the database server.

</td>
</tr>
<tr>
<td valign="top">

IsService

</td>
<td valign="top">

Whether the database server is running as a service.

</td>
</tr>
<tr>
<td valign="top">

JavaVM

</td>
<td valign="top">

An empty string if the database server uses one Java VM per database. If the database server uses one Java VM for all databases, this property indicates the path to the JAVA executable.

</td>
</tr>
<tr>
<td valign="top">

Language

</td>
<td valign="top">

The locale language for the server.

</td>
</tr>
<tr>
<td valign="top">

LastConnectionProperty

</td>
<td valign="top">

The number that represents the last connection property.

</td>
</tr>
<tr>
<td valign="top">

LastDatabaseProperty

</td>
<td valign="top">

The number that represents the last database property.

</td>
</tr>
<tr>
<td valign="top">

LastOption

</td>
<td valign="top">

The number that represents the last connection property that corresponds to a database option.

</td>
</tr>
<tr>
<td valign="top">

LastServerProperty

</td>
<td valign="top">

The number that represents the last server property.

</td>
</tr>
<tr>
<td valign="top">

LegalCopyright

</td>
<td valign="top">

The copyright string for the software.

</td>
</tr>
<tr>
<td valign="top">

LegalTrademarks

</td>
<td valign="top">

The trademark information for the software.

</td>
</tr>
<tr>
<td valign="top">

LivenessTimeout

</td>
<td valign="top">

The client liveness timeout default.

</td>
</tr>
<tr>
<td valign="top">

LockedCursorPages

</td>
<td valign="top">

The number of pages used to keep cursor heaps pinned in memory.

</td>
</tr>
<tr>
<td valign="top">

LockedHeapPages

</td>
<td valign="top">

The number of heap pages locked in the cache.

</td>
</tr>
<tr>
<td valign="top">

MachineName

</td>
<td valign="top">

The name of the computer running a database server. Typically, this is the computer's host name.

</td>
</tr>
<tr>
<td valign="top">

MainHeapBytes

</td>
<td valign="top">

The amount of memory allocated for server data structures, in bytes.

</td>
</tr>
<tr>
<td valign="top">

MainHeapPages

</td>
<td valign="top">

The amount of memory allocated for server data structures, in database pages.

</td>
</tr>
<tr>
<td valign="top">

MapPhysicalMemoryEng

</td>
<td valign="top">

The number of database page address space windows mapped to physical memory in the cache using Address Windowing Extensions.

</td>
</tr>
<tr>
<td valign="top">

MaxCacheSize

</td>
<td valign="top">

The maximum cache size allowed, in kilobytes.

</td>
</tr>
<tr>
<td valign="top">

MaxConnections

</td>
<td valign="top">

The maximum number of concurrent connections that the database server allows. The default value can be lowered using the -gm server option.

</td>
</tr>
<tr>
<td valign="top">

MaxEventType

</td>
<td valign="top">

The maximum valid event type ID.

</td>
</tr>
<tr>
<td valign="top">

MaxMessage

</td>
<td valign="top">

This property is deprecated. The current maximum line number that can be retrieved from the database server messages window. This represents the most recent message displayed in the database server messages window.

</td>
</tr>
<tr>
<td valign="top">

MaxMirrorBackgroundWorkers

</td>
<td valign="top">

The highest number of workers used for database mirroring background tasks since the server started. These workers are separate from those controlled by the multiprogramming level.

</td>
</tr>
<tr>
<td valign="top">

MaxMultiProgrammingLevel

</td>
<td valign="top">

The maximum number of tasks that the database server can process concurrently. When AutoMultiProgrammingLevel is enabled, the server may increase the multiprogramming level up to this value.

</td>
</tr>
<tr>
<td valign="top">

MaxRemoteCapability

</td>
<td valign="top">

The maximum valid capability ID.

</td>
</tr>
<tr>
<td valign="top">

MaxTableDefCacheSize

</td>
<td valign="top">

The upper limit on the amount of memory consumed by table definition objects. The minimum value is 512 KB.

</td>
</tr>
<tr>
<td valign="top">

Message, `linenumber` 

</td>
<td valign="top">

A line from the database server messages window, prefixed by the date and time the message appeared. The second parameter specifies the line number. This property is deprecated.

The value for `PROPERTY( "message" )` is the first line of output that was written to the database server messages window. Calling `PROPERTY( "message", n )` The *nth* line of server output \(with zero being the first line\). The buffer is finite, so as messages are generated, the first lines are dropped and may no longer be available in memory. In this case, the value is NULL.

</td>
</tr>
<tr>
<td valign="top">

MessageCategoryLimit

</td>
<td valign="top">

The minimum number of messages of each severity and category that can be retrieved using the sa\_server\_messages system procedure. The default value is 400.

</td>
</tr>
<tr>
<td valign="top">

MessageText, `linenumber` 

</td>
<td valign="top">

This property is deprecated. The text associated with the specified line number in the database server messages window, without a date and time prefix. The second parameter specifies the line number.

</td>
</tr>
<tr>
<td valign="top">

MessageTime, `linenumber` 

</td>
<td valign="top">

This property is deprecated. The date and time associated with the specified line number in the database server messages window. The second parameter specifies the line number.

</td>
</tr>
<tr>
<td valign="top">

MessageWindowSize

</td>
<td valign="top">

This property is deprecated. The maximum number of lines that can be retrieved from the database server messages window.

</td>
</tr>
<tr>
<td valign="top">

MinCacheSize

</td>
<td valign="top">

The minimum cache size allowed, in kilobytes.

</td>
</tr>
<tr>
<td valign="top">

MiniDumpType

</td>
<td valign="top">

The current setting for the crash dump type.

</td>
</tr>
<tr>
<td valign="top">

MinMultiProgrammingLevel

</td>
<td valign="top">

The minimum number of tasks that the server can process concurrently. When AutoMultiProgrammingLevel is enabled, the server may decrease the multiprogramming level down to this value.

</td>
</tr>
<tr>
<td valign="top">

MultiPacketsReceived

</td>
<td valign="top">

The number of multi-packet requests received during client/server communications.

</td>
</tr>
<tr>
<td valign="top">

MultiPacketsSent

</td>
<td valign="top">

The number of multi-packet responses sent during client/server communications.

</td>
</tr>
<tr>
<td valign="top">

MultiPageAllocs

</td>
<td valign="top">

The number of multi-page cache allocations.

</td>
</tr>
<tr>
<td valign="top">

MultiProgrammingLevel

</td>
<td valign="top">

The current maximum number of concurrent tasks the server will process simultaneously. Requests are queued if there are more concurrent tasks than this value. This can be changed with the -gn server option.

</td>
</tr>
<tr>
<td valign="top">

Name

</td>
<td valign="top">

The alternate name of the server used to connect to the database if one was specified, otherwise, The real server name.

If the client is connected to a copy node and specified NodeType=COPY in the connection string, then the value of this property may be different from the database server name specified in the client connection string by the ServerName connection parameter.

</td>
</tr>
<tr>
<td valign="top">

NativeProcessorArchitecture

</td>
<td valign="top">

A string that identifies the native processor type on which the software is running. For platforms where a processor can be emulated \(such as x86 on x64\), the actual processor type - not the OS architecture type - is returned.

The value does not indicate whether the operating system is 32-bit or 64-bit.

The following are possible values for Linux: X86, X86\_64, ARM, ARM\_64

X86 represents a 32-bit hardware architecture. X86\_64 represents a 64-bit hardware architecture.

</td>
</tr>
<tr>
<td valign="top">

NumLogicalProcessors

</td>
<td valign="top">

The number of logical processors \(including cores and hyperthreads\) enabled on the server computer.

</td>
</tr>
<tr>
<td valign="top">

NumLogicalProcessorsUsed

</td>
<td valign="top">

The number of logical processors the database server will use.

</td>
</tr>
<tr>
<td valign="top">

NumPhysicalProcessors

</td>
<td valign="top">

The number of physical processors enabled on the server computer. This value is NumLogicalProcessors divided by the number of cores or hyperthreads per physical processor. On some platforms, cores or hyperthreads may be counted as physical processors.

</td>
</tr>
<tr>
<td valign="top">

NumPhysicalProcessorsUsed

</td>
<td valign="top">

The number of physical processors the database server will use.

</td>
</tr>
<tr>
<td valign="top">

ObjectType

</td>
<td valign="top">

The type of database object. This value is used by the SYSOBJECT system view.

</td>
</tr>
<tr>
<td valign="top">

ODataAddresses

</td>
<td valign="top">

A semicolon-delimited list of the TCP/IP addresses and ports that the OData server is using to listen for OData connections.

</td>
</tr>
<tr>
<td valign="top">

ODataSecureAddresses

</td>
<td valign="top">

A semicolon-delimited lists of TCP/IP address and ports that the OData server is using to listen for secure OData connections.

</td>
</tr>
<tr>
<td valign="top">

OmniIdentifier

</td>
<td valign="top">

Reserved for system use.

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

PageSize

</td>
<td valign="top">

The size of the database server cache pages. This can be set using the -gp option, otherwise, it is the maximum database page size of the databases specified on the command line.

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

PeakCacheSize

</td>
<td valign="top">

The largest value the cache has reached in the current session, in kilobytes.

</td>
</tr>
<tr>
<td valign="top">

PlanStatisticsStored

</td>
<td valign="top">

For internal use only.

</td>
</tr>
<tr>
<td valign="top">

PlanStatisticsStoredMax

</td>
<td valign="top">

For internal use only.

</td>
</tr>
<tr>
<td valign="top">

Platform

</td>
<td valign="top">

The operating system on which the software is running.

</td>
</tr>
<tr>
<td valign="top">

PlatformVer

</td>
<td valign="top">

The operating system on which the software is running, including build numbers, service packs, and so on.

</td>
</tr>
<tr>
<td valign="top">

PrepStmt

</td>
<td valign="top">

The number of prepared statements currently being maintained by the database server for all databases and connections.

</td>
</tr>
<tr>
<td valign="top">

ProcessCPU

</td>
<td valign="top">

The CPU usage for the database server process. Values are in seconds.

The value is cumulative since the database server was started. The value will not match the instantaneous value displayed in applications such as the Performance Monitor.

</td>
</tr>
<tr>
<td valign="top">

ProcessCPUSystem

</td>
<td valign="top">

The CPU usage for the database server process CPU. This is the amount of CPU time that the database server spent inside the operating system kernel. Values are in seconds.

The value is cumulative since the database server was started. The value will not match the instantaneous value displayed in applications such as the Performance Monitor.

</td>
</tr>
<tr>
<td valign="top">

ProcessCPUUser

</td>
<td valign="top">

User CPU usage for the database server process. Values are in seconds. This excludes the amount of CPU time that the database server spent inside the operating system kernel.

The value is cumulative since the database server was started. The value will not match the instantaneous value displayed in applications such as the Performance Monitor.

</td>
</tr>
<tr>
<td valign="top">

ProcessID

</td>
<td valign="top">

The process ID of the database server process.

</td>
</tr>
<tr>
<td valign="top">

ProcessorAffinity

</td>
<td valign="top">

The logical processors being used by the database server as specified by the sa\_server\_option system procedure and the ProcessorAffinity option.

</td>
</tr>
<tr>
<td valign="top">

ProcessorArchitecture

</td>
<td valign="top">

A string that identifies the processor type that the current software was built for.

The following are possible values for Linux: X86, X86\_64, ARM, ARM\_64

X86 represents a 32-bit database server. X86\_64 represents a 64-bit database server.

</td>
</tr>
<tr>
<td valign="top">

ProductName

</td>
<td valign="top">

The name of the software.

</td>
</tr>
<tr>
<td valign="top">

ProductVersion

</td>
<td valign="top">

The version of the software being run.

</td>
</tr>
<tr>
<td valign="top">

ProfileFilterConn

</td>
<td valign="top">

The ID of the connection being monitored if procedure profiling for a specific connection is turned on. If profiling is not turned on, the value is an empty string.

</td>
</tr>
<tr>
<td valign="top">

ProfileFilterUser

</td>
<td valign="top">

The user ID being monitored if procedure profiling for a specific user is turned on. If procedure profiling for a specific user is not turned on, the value is an empty string.

</td>
</tr>
<tr>
<td valign="top">

PropertyHistoryList

</td>
<td valign="top">

The current minimal set of properties being tracked.

</td>
</tr>
<tr>
<td valign="top">

PropertyHistoryListActual

</td>
<td valign="top">

The current set of properties being tracked.

</td>
</tr>
<tr>
<td valign="top">

PropertyHistorySize

</td>
<td valign="top">

Indicates either the minimum amount of time to store tracked property values or the maximum amount of memory to use to store tracked property values.

</td>
</tr>
<tr>
<td valign="top">

PropertyHistorySizeBytes

</td>
<td valign="top">

The current amount of memory, in bytes, that is currently being used for property history tracking.

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

QueryMemActiveCurr

</td>
<td valign="top">

The number of requests actively using query memory.

</td>
</tr>
<tr>
<td valign="top">

QueryMemActiveEst

</td>
<td valign="top">

The database server's estimate of the steady state average of the number of requests actively using query memory.

</td>
</tr>
<tr>
<td valign="top">

QueryMemActiveMax

</td>
<td valign="top">

The maximum number of requests that are allowed to actively use query memory.

</td>
</tr>
<tr>
<td valign="top">

QueryMemExtraAvail

</td>
<td valign="top">

The number of pages available to grant beyond the base memory-intensive grant.

</td>
</tr>
<tr>
<td valign="top">

QueryMemGrantBase

</td>
<td valign="top">

The minimum number of pages granted to all requests.

</td>
</tr>
<tr>
<td valign="top">

QueryMemGrantBaseMI

</td>
<td valign="top">

The minimum number of pages granted to memory-intensive requests.

</td>
</tr>
<tr>
<td valign="top">

QueryMemGrantExtra

</td>
<td valign="top">

The number of query memory pages that can be distributed among active memory-intensive requests beyond QueryMemGrantBaseMI.

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

QueryMemPages

</td>
<td valign="top">

The number of pages available for query execution algorithms.

</td>
</tr>
<tr>
<td valign="top">

QueryMemPercentOfCache

</td>
<td valign="top">

The percentage of maximum cache size available for query execution algorithms.

</td>
</tr>
<tr>
<td valign="top">

QuittingTime

</td>
<td valign="top">

The shutdown time for the server. If none is specified, the value is none. If the database has the time\_zone option set, then the value is returned using the database's time zone.

</td>
</tr>
<tr>
<td valign="top">

RememberLastPlan

</td>
<td valign="top">

Whether the database server is recording the last query optimization plan returned by the optimizer.

</td>
</tr>
<tr>
<td valign="top">

RememberLastStatement

</td>
<td valign="top">

Whether the database server is recording the last statement prepared by each connection.

</td>
</tr>
<tr>
<td valign="top">

RemoteCapability

</td>
<td valign="top">

The remote capability name associated with a given capability ID.

</td>
</tr>
<tr>
<td valign="top">

RemoteputWait

</td>
<td valign="top">

The number of times the server had to block while sending a communication packet. Typically, blocking only occurs if the database server is sending data faster than the client or network can receive it. It does not indicate an error condition.

</td>
</tr>
<tr>
<td valign="top">

Req

</td>
<td valign="top">

The number of times the server has been asked to handle a new request or continue processing an existing request.

</td>
</tr>
<tr>
<td valign="top">

ReqCountActive

</td>
<td valign="top">

The number of active requests.

</td>
</tr>
<tr>
<td valign="top">

ReqCountBlockContention

</td>
<td valign="top">

The number of times that any connection has blocked due to contention for an internal server resource.

</td>
</tr>
<tr>
<td valign="top">

ReqCountBlockIO

</td>
<td valign="top">

The number of times that any connection has blocked while waiting for an IO request to complete.

</td>
</tr>
<tr>
<td valign="top">

ReqCountBlockLock

</td>
<td valign="top">

The number of times that any connection has blocked while waiting for a row lock held by another connection.

</td>
</tr>
<tr>
<td valign="top">

ReqCountUnscheduled

</td>
<td valign="top">

The number of times that any connection has blocked while waiting for a server thread to process it.

</td>
</tr>
<tr>
<td valign="top">

ReqTimeActive

</td>
<td valign="top">

The total amount of time in seconds that the server has spent directly servicing requests.

</td>
</tr>
<tr>
<td valign="top">

ReqTimeBlockContention

</td>
<td valign="top">

The total amount of time in seconds that any connection has blocked due to contention for an internal server resource.

</td>
</tr>
<tr>
<td valign="top">

ReqTimeBlockIO

</td>
<td valign="top">

The total amount of time in seconds that any connection has blocked while waiting for an IO request to complete.

</td>
</tr>
<tr>
<td valign="top">

ReqTimeBlockLock

</td>
<td valign="top">

The total amount of time in seconds that any connection has blocked while waiting for a row lock held by another connection.

</td>
</tr>
<tr>
<td valign="top">

ReqTimeUnscheduled

</td>
<td valign="top">

The total amount of time in seconds that any connection has blocked while waiting for a server thread to process it.

</td>
</tr>
<tr>
<td valign="top">

RequestFilterConn

</td>
<td valign="top">

The ID of the connection that logging information is being filtered for. If no filtering is being performed, the value is -1.

</td>
</tr>
<tr>
<td valign="top">

RequestFilterDB

</td>
<td valign="top">

The ID of the database that logging information is being filtered for. If no filtering is being performed, the value is -1.

</td>
</tr>
<tr>
<td valign="top">

RequestLogFile

</td>
<td valign="top">

The name of the request logging file, or an empty string if there is no request logging.

</td>
</tr>
<tr>
<td valign="top">

RequestLogging

</td>
<td valign="top">

The current setting for request logging. Values can be one of SQL, PLAN, HOSTVARS, PROCEDURES, TRIGGERS, OTHER, BLOCKS, REPLACE, ALL, or NONE.

</td>
</tr>
<tr>
<td valign="top">

RequestLogMaxSize

</td>
<td valign="top">

The maximum size of the request log file.

</td>
</tr>
<tr>
<td valign="top">

RequestLogNumFiles

</td>
<td valign="top">

The number of request log files being kept.

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

RequestTiming

</td>
<td valign="top">

Whether logging of request timing information is turned on. The logging of request timing information is turned on using the -zt database server option.

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

SendFail

</td>
<td valign="top">

The number of times that the underlying communications protocols have failed to send a packet.

</td>
</tr>
<tr>
<td valign="top">

ServerEdition

</td>
<td valign="top">

A space-separated list of words describing the database server type. Values include:

-   Evaluation
-   Developer
-   Web
-   Educational
-   Standard
-   Advanced
-   Workgroup
-   OEM
-   Authenticated




</td>
</tr>
<tr>
<td valign="top">

ServerName

</td>
<td valign="top">

The real server name \(never an alternate server name\). You can use this value to determine which of the operational servers is currently acting as primary in a database mirroring configuration.

</td>
</tr>
<tr>
<td valign="top">

SharedMemoryListener

</td>
<td valign="top">

Whether the database server is accepting shared memory connections, and No otherwise.

</td>
</tr>
<tr>
<td valign="top">

SingleCLR

</td>
<td valign="top">

The version number of the CLR if the database server uses a single CLR external environment for all databases or NONE if the database server uses one CLR external environment per database when executing CLR stored procedures.

</td>
</tr>
<tr>
<td valign="top">

SingleJVM

</td>
<td valign="top">

Whether the database server uses a single Java VM for all databases running on the database server \(Yes\), or whether the database server uses one Java VM per database when executing Java stored procedures \(No\).

</td>
</tr>
<tr>
<td valign="top">

StartDBPermission

</td>
<td valign="top">

The setting of the -gd server option, which can be one of DBA, all, or none.

</td>
</tr>
<tr>
<td valign="top">

StartTime

</td>
<td valign="top">

The date/time that the server started. If the database has the time\_zone option set, then the value is returned using the database's time zone.

</td>
</tr>
<tr>
<td valign="top">

StatisticsCleaner

</td>
<td valign="top">

Enable statistics cleaner to fix statistics that give bad estimates by performing scans on the table.

</td>
</tr>
<tr>
<td valign="top">

StreamsUsed

</td>
<td valign="top">

The number of database server streams in use.

</td>
</tr>
<tr>
<td valign="top">

TcpIpAddresses

</td>
<td valign="top">

A semicolon-delimited list of the IP addresses that the server is listening to for Command Sequence and TDS connections from clients. For example:

```
(::1):2638;127.0.0.1:2638
```



</td>
</tr>
<tr>
<td valign="top">

TcpIpListeners

</td>
<td valign="top">

A semicolon-delimited list of IP addresses and IP address:port pairs that the database server is using to listen for TCP/IP connections.

</td>
</tr>
<tr>
<td valign="top">

TempDir

</td>
<td valign="top">

The directory in which temporary files are stored by the server.

</td>
</tr>
<tr>
<td valign="top">

ThreadDeadlocksAvoided

</td>
<td valign="top">

The number of times a thread deadlock error was detected but not reported to client applications. When the database server starts, the value of this property is 0.

To avoid thread deadlock errors, the database server dynamically increases the multiprogramming level. If the multiprogramming level cannot be increased, a thread deadlock error is returned to the client application and the ThreadDeadlocksReported property is incremented.

</td>
</tr>
<tr>
<td valign="top">

ThreadDeadlocksReported

</td>
<td valign="top">

The number of times a thread deadlock error was reported to client applications. When the database server starts, the value of this property is 0.

</td>
</tr>
<tr>
<td valign="top">

TimeZoneAdjustment

</td>
<td valign="top">

The number of minutes that must be added to the Coordinated Universal Time \(UTC\) to display time local to the server.

</td>
</tr>
<tr>
<td valign="top">

TopologyAwareScheduling

</td>
<td valign="top">

Whether topology aware scheduling is in use.

</td>
</tr>
<tr>
<td valign="top">

TotalBuffers

</td>
<td valign="top">

The total number of network buffers.

</td>
</tr>
<tr>
<td valign="top">

UniqueClientAddresses

</td>
<td valign="top">

The number of unique client network addresses connected to a network server, excluding shared memory and local TCP/IP connections.

</td>
</tr>
<tr>
<td valign="top">

UnschReq

</td>
<td valign="top">

The number of requests that are currently queued up waiting for an available server worker.

</td>
</tr>
<tr>
<td valign="top">

UserDefinedCounterRate01

</td>
<td valign="top">

The current value of the user-defined performance counter. The semantics of this property are defined by the client application. This counter can also be accessed from the Performance Monitor. The Performance Monitor displays the change in the value of the counter over time.

</td>
</tr>
<tr>
<td valign="top">

UserDefinedCounterRate02

</td>
<td valign="top">

The current value of the user-defined performance counter. The semantics of this property are defined by the client application. This counter can also be accessed from the Performance Monitor. The Performance Monitor displays the change in the value of the counter over time.

</td>
</tr>
<tr>
<td valign="top">

UserDefinedCounterRate03

</td>
<td valign="top">

The current value of the user-defined performance counter. The semantics of this property are defined by the client application. This counter can also be accessed from the Performance Monitor. The Performance Monitor displays the change in the value of the counter over time.

</td>
</tr>
<tr>
<td valign="top">

UserDefinedCounterRate04

</td>
<td valign="top">

The current value of the user-defined performance counter. The semantics of this property are defined by the client application. This counter can also be accessed from the Performance Monitor. The Performance Monitor displays the change in the value of the counter over time.

</td>
</tr>
<tr>
<td valign="top">

UserDefinedCounterRate05

</td>
<td valign="top">

The current value of the user-defined performance counter. The semantics of this property are defined by the client application. This counter can also be accessed from the Performance Monitor. The Performance Monitor displays the change in the value of the counter over time.

</td>
</tr>
<tr>
<td valign="top">

UserDefinedCounterRaw01

</td>
<td valign="top">

The current value of the user-defined performance counter. The semantics of this property are defined by the client application. This counter can also be accessed from the Performance Monitor. The Performance Monitor displays the absolute value of the counter.

</td>
</tr>
<tr>
<td valign="top">

UserDefinedCounterRaw02

</td>
<td valign="top">

The current value of the user-defined performance counter. The semantics of this property are defined by the client application. This counter can also be accessed from the Performance Monitor. The Performance Monitor displays the absolute value of the counter.

</td>
</tr>
<tr>
<td valign="top">

UserDefinedCounterRaw03

</td>
<td valign="top">

The current value of the user-defined performance counter. The semantics of this property are defined by the client application. This counter can also be accessed from the Performance Monitor. The Performance Monitor displays the absolute value of the counter.

</td>
</tr>
<tr>
<td valign="top">

UserDefinedCounterRaw04

</td>
<td valign="top">

The current value of the user-defined performance counter. The semantics of this property are defined by the client application. This counter can also be accessed from the Performance Monitor. The Performance Monitor displays the absolute value of the counter.

</td>
</tr>
<tr>
<td valign="top">

UserDefinedCounterRaw05

</td>
<td valign="top">

The current value of the user-defined performance counter. The semantics of this property are defined by the client application. This counter can also be accessed from the Performance Monitor. The Performance Monitor displays the absolute value of the counter.

</td>
</tr>
<tr>
<td valign="top">

WebClientLogFile

</td>
<td valign="top">

The name of the web service client log file.

</td>
</tr>
<tr>
<td valign="top">

WebClientLogging

</td>
<td valign="top">

Whether web service client information is being logged to a file.

</td>
</tr>
</table>

