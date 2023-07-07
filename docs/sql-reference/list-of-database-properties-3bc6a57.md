<!-- loio3bc6a5766c5f1014a1b8e1f06f9b86e0 -->

# List of Database Properties

Database properties are available for each connection to a database. Use the DB\_PROPERTY system function to retrieve the value for an individual database property, or the sa\_db\_properties system procedure to retrieve the values of all database properties.



The following statement returns the page size of the current database:

```
SELECT DB_PROPERTY ( 'PageSize' );
```

Use the sa\_db\_properties system procedure to retrieve the values of all database properties:

```
CALL sa_db_properties;
```



## Database Properties


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

AccentSensitive



</td>
<td valign="top">

Whether the database is accent sensitive \(On\) or not \(Off\). The value is FRENCH if the database uses French sensitivity rules.



</td>
</tr>
<tr>
<td valign="top">

Alias



</td>
<td valign="top">

The database name.



</td>
</tr>
<tr>
<td valign="top">

AlternateMirrorServerName



</td>
<td valign="top">

The alternate mirror server name associated with the database if one was specified.



</td>
</tr>
<tr>
<td valign="top">

AlternateServerName



</td>
<td valign="top">

The alternate server name associated with the database if one was specified.



</td>
</tr>
<tr>
<td valign="top">

ApproximateCPUTime



</td>
<td valign="top">

An estimate of the amount of CPU time accumulated by the database, in seconds. The value may differ from the actual value by as much as 50 percent, although typical variations are in the 5 to 10 percent range. On multi-processor computers, each CPU \(or hyperthread or core\) accumulates time, so the sum of accumulated times for all connections may be greater than the elapsed time.



</td>
</tr>
<tr>
<td valign="top">

ArbiterState



</td>
<td valign="top">

The state of the arbiter server. When the database you are connected to is not mirrored, this property is *NULL*. Otherwise this property is *connected* when the arbiter server is connected to the primary server, or *disconnected* when it is not connected to the primary server.



</td>
</tr>
<tr>
<td valign="top">

AuditingTypes



</td>
<td valign="top">

The types of auditing currently enabled.



</td>
</tr>
<tr>
<td valign="top">

Authenticated



</td>
<td valign="top">

Whether the database has been authenticated.



</td>
</tr>
<tr>
<td valign="top">

BackupInProgress



</td>
<td valign="top">

Whether the database is currently being backed up.



</td>
</tr>
<tr>
<td valign="top">

BlankPadding



</td>
<td valign="top">

Whether the database has blank padding enabled.



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

The number of database page lookups satisfied by finding the page in the cache.



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

Capabilities



</td>
<td valign="top">

The capability bits enabled for the database. This property is primarily for use by Technical Support.



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

CaseSensitive



</td>
<td valign="top">

Whether the database is case sensitive \(On\) or not \(Off\).



</td>
</tr>
<tr>
<td valign="top">

CatalogCollation



</td>
<td valign="top">

The identifier for the collation used for the catalog. This property has extensions that you can specify when querying the property value with the DB\_EXTENDED\_PROPERTY function.



</td>
</tr>
<tr>
<td valign="top">

CharSet



</td>
<td valign="top">

The CHAR character set of the database. This property has extensions that you can specify when querying the property value with the DB\_EXTENDED\_PROPERTY function.



</td>
</tr>
<tr>
<td valign="top">

CheckpointLogCommitToDisk



</td>
<td valign="top">

The number of checkpoint log commits to disk.



</td>
</tr>
<tr>
<td valign="top">

CheckpointLogPagesInUse



</td>
<td valign="top">

The number of checkpoint log pages in use.



</td>
</tr>
<tr>
<td valign="top">

CheckpointLogPagesRelocated



</td>
<td valign="top">

The number of relocated checkpoint log pages.



</td>
</tr>
<tr>
<td valign="top">

CheckpointLogPagesWritten



</td>
<td valign="top">

The number of checkpoint log pages that have been written.



</td>
</tr>
<tr>
<td valign="top">

CheckpointLogSavePreimage



</td>
<td valign="top">

The number of preimages of database pages that are being added to the checkpoint log.



</td>
</tr>
<tr>
<td valign="top">

CheckpointLogSize



</td>
<td valign="top">

The size of the checkpoint log, in pages.



</td>
</tr>
<tr>
<td valign="top">

CheckpointLogWrites



</td>
<td valign="top">

The number of writes to the checkpoint log.



</td>
</tr>
<tr>
<td valign="top">

CheckpointUrgency



</td>
<td valign="top">

The time that has elapsed since the last checkpoint, as a percentage of the checkpoint time setting of the database.



</td>
</tr>
<tr>
<td valign="top">

Checksum



</td>
<td valign="top">

Whether global checksums are enabled for the database \(a checksum is created for each database page\). Checksums are always present for critical pages.



</td>
</tr>
<tr>
<td valign="top">

Chkpt



</td>
<td valign="top">

The number of checkpoints that have been performed.



</td>
</tr>
<tr>
<td valign="top">

ChkptFlush



</td>
<td valign="top">

The number of ranges of adjacent pages written out during a checkpoint.



</td>
</tr>
<tr>
<td valign="top">

ChkptPage



</td>
<td valign="top">

The number of transaction log checkpoints.



</td>
</tr>
<tr>
<td valign="top">

CleanablePagesAdded



</td>
<td valign="top">

The number of pages marked to be cleaned since database server startup.



</td>
</tr>
<tr>
<td valign="top">

CleanablePagesCleaned



</td>
<td valign="top">

The number of database pages cleaned since database server startup.



</td>
</tr>
<tr>
<td valign="top">

CleanableRowsAdded



</td>
<td valign="top">

The number of rows marked to be deleted since database server startup.



</td>
</tr>
<tr>
<td valign="top">

CleanableRowsCleaned



</td>
<td valign="top">

The number of shadow table rows deleted since database server startup.



</td>
</tr>
<tr>
<td valign="top">

ClientStmtCacheHits



</td>
<td valign="top">

The number of prepares that were not required for this database because of the client statement cache. This is the number of additional prepares that would be required if client statement caching was disabled.



</td>
</tr>
<tr>
<td valign="top">

ClientStmtCacheMisses



</td>
<td valign="top">

The number of statements in the client statement cache for this database that were prepared again. This is the number of times a cached statement was considered for reuse, but could not be reused because of a schema change, a database option setting, or a DROP VARIABLE statement.



</td>
</tr>
<tr>
<td valign="top">

Collation



</td>
<td valign="top">

The collation used by the database. This property has extensions that you can specify when querying the property value.



</td>
</tr>
<tr>
<td valign="top">

Commit



</td>
<td valign="top">

The number of times the server has forced a flush of the disk cache.



</td>
</tr>
<tr>
<td valign="top">

CommitFile



</td>
<td valign="top">

The number of times the server has forced a flush of the disk cache.



</td>
</tr>
<tr>
<td valign="top">

ConnCount



</td>
<td valign="top">

The number of connections to the database. The property value does not include connections used for internal operations, but it does include connections used for events and external environment support. To obtain an accurate count of the number of connections in use, execute the following statement: `SELECT COUNT( * ) FROM sa_conn_info( ) WHERE number < 100000000;` 



</td>
</tr>
<tr>
<td valign="top">

ConnectedTime



</td>
<td valign="top">

The total length of time, in seconds, that all connections have been connected to the database. The value is updated only when a request completes for a connection or when a connection disconnects. As a result, the value can lag behind for connections that are idle or busy executing for a long time in the database server. The value includes time accrued by any connection, including database events and background server connections \(such as the database cleaner\).



</td>
</tr>
<tr>
<td valign="top">

ConnPoolCachedCount



</td>
<td valign="top">

The number of connections disconnected by the application but cached for connection pooling.



</td>
</tr>
<tr>
<td valign="top">

ConnPoolHits



</td>
<td valign="top">

The number of reused pooled connections.



</td>
</tr>
<tr>
<td valign="top">

ConnPoolMisses



</td>
<td valign="top">

The number of pooled connections which were cached but could not be reused.



</td>
</tr>
<tr>
<td valign="top">

ConnsDisabled



</td>
<td valign="top">

Whether connections to the current database are disabled \(On\) or not \(Off\).



</td>
</tr>
<tr>
<td valign="top">

CopyNodeParent



</td>
<td valign="top">

The name of the current parent server of a copy node in a read-only scale-out configuration.



</td>
</tr>
<tr>
<td valign="top">

CurrentRedoPos



</td>
<td valign="top">

The current offset in the transaction log file where the next database operation is to be logged.



</td>
</tr>
<tr>
<td valign="top">

CurrentTableDefCacheSize



</td>
<td valign="top">

The current amount of memory consumed by table definition objects.



</td>
</tr>
<tr>
<td valign="top">

CurrentTimelineID



</td>
<td valign="top">

For internal use only.



</td>
</tr>
<tr>
<td valign="top">

CurrentTimelineSignature



</td>
<td valign="top">

For internal use only.



</td>
</tr>
<tr>
<td valign="top">

CurrentTimezoneOffset



</td>
<td valign="top">

The number of minutes that the database is ahead of Coordinated Universal Time \(UTC\).



</td>
</tr>
<tr>
<td valign="top">

CurrIO



</td>
<td valign="top">

The current number of file I/Os that were issued by the server but haven't yet completed.



</td>
</tr>
<tr>
<td valign="top">

CurrRead



</td>
<td valign="top">

The current number of file reads that were issued by the server, but haven't yet completed.



</td>
</tr>
<tr>
<td valign="top">

CurrWrite



</td>
<td valign="top">

The current number of file writes that were issued by the server, but haven't yet completed.



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

DatabaseCleaner



</td>
<td valign="top">

Whether the database cleaner is enabled.



</td>
</tr>
<tr>
<td valign="top">

IsBooleanSupportEnabled



</td>
<td valign="top">

Whether the BOOLEAN type is supported.



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

DiskRetryReadScatter



</td>
<td valign="top">

The number of disk read retries for scattered reads.



</td>
</tr>
<tr>
<td valign="top">

DiskSandbox



</td>
<td valign="top">

Whether the read-write file operations of the database are restricted to the directory where the main database file is located.



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

The number of disk gather write hints.



</td>
</tr>
<tr>
<td valign="top">

DriveBus



</td>
<td valign="top">

The type of bus to which the database file is connected: one of Unknown, SCSI, ATAPI, ATA, 1394, SSA, Fibre, USB, RAID, iSCSI, SAS, SATA, SD, MMC, Virtual, FileBackedVirtual. If the bus type cannot be determined, this property is NULL. The value of this property for the primary dbspace is recorded in the SYSHISTORY view.



</td>
</tr>
<tr>
<td valign="top">

DriveModel



</td>
<td valign="top">

The model number of the drive on which the database is located. The value of this property for the primary dbspace is recorded in the SYSHISTORY view. If the drive model cannot be determined, this property is NULL.



</td>
</tr>
<tr>
<td valign="top">

DriveType



</td>
<td valign="top">

The type of drive on which the database file is located: one of CD, FIXED, RAMDISK, REMOTE, REMOVABLE, UNKNOWN. This property has extensions that you can specify when querying the property value with the DB\_EXTENDED\_PROPERTY function. Depending on the version of Linux and the type of drive, it may not be possible to determine the drive type. In these cases the value is UNKNOWN.



</td>
</tr>
<tr>
<td valign="top">

Encryption



</td>
<td valign="top">

The type of encryption used for database encryption: AES256CTR \(AES256 for older databases\).



</td>
</tr>
<tr>
<td valign="top">

EncryptionScope



</td>
<td valign="top">

The part of the database, if any, that can be encrypted. TABLE indicates that table encryption is enabled. DATABASE indicates that the whole database is encrypted. NONE indicates that table encryption is not enabled, and the database is not encrypted.



</td>
</tr>
<tr>
<td valign="top">

ExprCacheAbandons



</td>
<td valign="top">

The number of times that the expression cache was completely abandoned because the hit rate was too low.



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

The number of lookups performed in the expression cache.



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

The number of times the expression cache was started.



</td>
</tr>
<tr>
<td valign="top">

ExtendDB



</td>
<td valign="top">

The number of pages by which the database file has been extended.



</td>
</tr>
<tr>
<td valign="top">

ExtendTempWrite



</td>
<td valign="top">

The number of pages by which temporary files have been extended.



</td>
</tr>
<tr>
<td valign="top">

File



</td>
<td valign="top">

The file name of the database root file, including path. This property has extensions that you can specify when querying the property value with the DB\_EXTENDED\_PROPERTY function.



</td>
</tr>
<tr>
<td valign="top">

FileSize



</td>
<td valign="top">

The file size of the system dbspace, in pages. This property has extensions that you can specify when querying the property value with the DB\_EXTENDED\_PROPERTY function.



</td>
</tr>
<tr>
<td valign="top">

FreePages



</td>
<td valign="top">

The number of free pages in the system dbspace. The FreePages property is only supported on databases created with version 8.0.0 or later. This property has extensions that you can specify when querying the property value with the DB\_EXTENDED\_PROPERTY function.



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

GlobalDBID



</td>
<td valign="top">

The value of the global\_database\_id option used to generate unique primary key values in a replication environment.



</td>
</tr>
<tr>
<td valign="top">

HasCollationTailoring



</td>
<td valign="top">

Whether collation tailoring was specified when the database was created. Possible values are On or Off.



</td>
</tr>
<tr>
<td valign="top">

HasEndianSwapFix



</td>
<td valign="top">

Whether the database supports both big-endian and little endian UTF-16 encoding on all platforms, regardless of the endianness of the platform. Possible values are On or Off.



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

HashWorkTables



</td>
<td valign="top">

The number of work tables created for hash-based operations.



</td>
</tr>
<tr>
<td valign="top">

HasNCHARLegacyCollationFix



</td>
<td valign="top">

Whether the database was created by using version 11 or later software, or by using a version 10 database server with the legacy collation fix and that uses a legacy NCHAR collation \(On\). The value is Off for databases created using a version 10 database server without the legacy collation fix, or databases created using a version 10 database server that do not use a legacy NCHAR collation.



</td>
</tr>
<tr>
<td valign="top">

HasQDADTTFeature



</td>
<td valign="top">

Whether the queue depth checking feature is available \(On\) or not \(Off\).



</td>
</tr>
<tr>
<td valign="top">

HasTornWriteFix



</td>
<td valign="top">

Whether the database has a fixed file format to allow recovery from partial writes.



</td>
</tr>
<tr>
<td valign="top">

HasX509AuthenticationSupport



</td>
<td valign="top">

Whether the server supports X.509 authentication..



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

HttpClientMultipleHeaders



</td>
<td valign="top">

Whether the database supports multiple headers with the same name in an HTTP result set.



</td>
</tr>
<tr>
<td valign="top">

HttpConnPoolCachedCount



</td>
<td valign="top">

The absolute count of cached database connections within all pools.



</td>
</tr>
<tr>
<td valign="top">

HttpConnPoolHits



</td>
<td valign="top">

The rate of connections reused by the same service.



</td>
</tr>
<tr>
<td valign="top">

HttpConnPoolMisses



</td>
<td valign="top">

The rate of new connections that were allocated when a connection could not be accessed from a pool. This property only counts HTTP requests to services that use connection pooling. At the time of access, a connection may not have been available due to a small pool size whose oldest connection did not fit the steal criteria.



</td>
</tr>
<tr>
<td valign="top">

HttpConnPoolSteals



</td>
<td valign="top">

The rate of connections taken by services where the connection belonged to another service. The service steals a connection from another service if the criteria is met for an HTTP request for a service not having any direct reusable connections and the pool size and age of the least used connection. A connection is allocated for the service and HttpConnPoolMisses is incremented instead if the pool criteria is not met.



</td>
</tr>
<tr>
<td valign="top">

IdentitySignature



</td>
<td valign="top">

This property is for internal use only.



</td>
</tr>
<tr>
<td valign="top">

IdentitySignatureUUID



</td>
<td valign="top">

This property is for internal use only.



</td>
</tr>
<tr>
<td valign="top">

IdleCheck



</td>
<td valign="top">

The number of times that the server's idle thread has become active to do idle writes, idle checkpoints, and so on.



</td>
</tr>
<tr>
<td valign="top">

IdleChkpt



</td>
<td valign="top">

The number of checkpoints completed by the server's idle thread. An idle checkpoint occurs whenever the idle thread writes out the last dirty page in the cache.



</td>
</tr>
<tr>
<td valign="top">

IdleChkTime



</td>
<td valign="top">

The number in hundredths of a second spent checkpointing during idle I/O.



</td>
</tr>
<tr>
<td valign="top">

IdleWrite



</td>
<td valign="top">

The number of disk writes that have been issued by the server's idle thread.



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

IOParallelism



</td>
<td valign="top">

The estimated number of simultaneous I/O operations supported by the dbspace. This property has extensions that you can specify when querying the property value with the DB\_EXTENDED\_PROPERTY function.



</td>
</tr>
<tr>
<td valign="top">

IOToRecover



</td>
<td valign="top">

The estimated number of I/O operations required to recover the database.



</td>
</tr>
<tr>
<td valign="top">

IQStore



</td>
<td valign="top">

This property is for internal use only.



</td>
</tr>
<tr>
<td valign="top">

IsTransactionalDDLEnabled



</td>
<td valign="top">

Whether the database server supports transactional DDL. auto\_commit must be disabled \(OFF\) before enabling autocommit\_DDL.



</td>
</tr>
<tr>
<td valign="top">

JavaVM



</td>
<td valign="top">

The Java VM the database server uses to execute Java in the database.



</td>
</tr>
<tr>
<td valign="top">

KeyDerivationIterations



</td>
<td valign="top">

The number of times that the database encryption key was hashed when the database was created.



</td>
</tr>
<tr>
<td valign="top">

Language



</td>
<td valign="top">

A comma-separated list of languages known to be supported by the database collation. The languages are in two-letter ISO format. If the language isn't known, the return value is NULL.



</td>
</tr>
<tr>
<td valign="top">

LastCheckpointTime



</td>
<td valign="top">

The date and time, in milliseconds, of the most recent checkpoint. If the database has the time\_zone option set, then the value is returned using the database's time zone.



</td>
</tr>
<tr>
<td valign="top">

LastCommitRedoPos



</td>
<td valign="top">

The redo log position after the last COMMIT operation was written to the transaction log by the database.



</td>
</tr>
<tr>
<td valign="top">

LastSyncedRedoPos



</td>
<td valign="top">

The last redo position for which a write was issued to disk and the data was synchronized to the physical medium. Data prior to this position is expected to be present on disk even in the event of a power failure.



</td>
</tr>
<tr>
<td valign="top">

LastWrittenRedoPos



</td>
<td valign="top">

The last redo position for which a write was issued to disk. The write is not necessarily synchronized to the physical medium as it may still be cached by the operating system, disk controller, or disk drive.



</td>
</tr>
<tr>
<td valign="top">

LockCount



</td>
<td valign="top">

The number of locks held by the database.



</td>
</tr>
<tr>
<td valign="top">

LockTablePages



</td>
<td valign="top">

The number of pages used to store lock information.



</td>
</tr>
<tr>
<td valign="top">

LogFreeCommit



</td>
<td valign="top">

The number of redo free commits. A redo free commit occurs when a commit of the transaction log is requested but the log has already been written \(so the commit was done for free\).



</td>
</tr>
<tr>
<td valign="top">

LogMirrorName



</td>
<td valign="top">

The file name of the transaction log mirror, including the path.



</td>
</tr>
<tr>
<td valign="top">

LogName



</td>
<td valign="top">

The file name of the transaction log, including path.



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

LTMGeneration



</td>
<td valign="top">

This property is for internal use only.



</td>
</tr>
<tr>
<td valign="top">

LTMTrunc



</td>
<td valign="top">

This property is for internal use only.



</td>
</tr>
<tr>
<td valign="top">

MaxConnections



</td>
<td valign="top">

The maximum number of concurrent connections that are allowed to the database. This property corresponds to the max\_connections database option.



</td>
</tr>
<tr>
<td valign="top">

MaxIO



</td>
<td valign="top">

The maximum value that CurrIO has reached.



</td>
</tr>
<tr>
<td valign="top">

MaxRead



</td>
<td valign="top">

The maximum value that CurrRead has reached.



</td>
</tr>
<tr>
<td valign="top">

MaxWrite



</td>
<td valign="top">

The maximum value that CurrWrite has reached.



</td>
</tr>
<tr>
<td valign="top">

MirrorMode



</td>
<td valign="top">

Whether database mirroring is not in use \(NULL\), or if the mirroring mode specified with the -xp option is synchronous or asynchronous.



</td>
</tr>
<tr>
<td valign="top">

MirrorRole



</td>
<td valign="top">

The role of the database server in a mirroring configuration. The value is Primary when the database is the primary database server or the mirror server. The value is Mirror when the database server is the mirror server. The value is Copy when the database server is a read-only mirror server that obtains its log pages from the current primary server, the current mirror server, or another read-only node.



</td>
</tr>
<tr>
<td valign="top">

MirrorServerState



</td>
<td valign="top">

The state of the mirror server. This property has extensions that you can specify when querying the property value with the DB\_EXTENDED\_PROPERTY function.



</td>
</tr>
<tr>
<td valign="top">

MirrorServerWaits



</td>
<td valign="top">

The number of times the database server waited more than 500 milliseconds when sending log pages to copy servers.



</td>
</tr>
<tr>
<td valign="top">

MirrorState



</td>
<td valign="top">

Information about the database's status in a mirroring configuration. This property has extensions that you can specify when querying the property value with the DB\_EXTENDED\_PROPERTY function.



</td>
</tr>
<tr>
<td valign="top">

MultiByteCharSet



</td>
<td valign="top">

Whether the database uses a multibyte character set, such as UTF-8, \(On\), or not \(Off\).



</td>
</tr>
<tr>
<td valign="top">

Name



</td>
<td valign="top">

The database name \(identical to Alias\).



</td>
</tr>
<tr>
<td valign="top">

NcharCharSet



</td>
<td valign="top">

The NCHAR character set of the database.



</td>
</tr>
<tr>
<td valign="top">

NcharCollation



</td>
<td valign="top">

The name of the collation used for NCHAR data. This property has extensions that you can specify when querying the property value.



</td>
</tr>
<tr>
<td valign="top">

NextScheduleTime



</td>
<td valign="top">

The next scheduled execution time for a specified event.This property has extensions that you can specify when querying the property value.



</td>
</tr>
<tr>
<td valign="top">

OptionWatchAction



</td>
<td valign="top">

The action that is taken when an attempt is made to set a database option that is included in the OptionWatchList property.



</td>
</tr>
<tr>
<td valign="top">

OptionWatchList



</td>
<td valign="top">

The list of database options being monitored by the database server.



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

PageRelocations



</td>
<td valign="top">

The number of relocatable heap pages that have been read from the temporary file.



</td>
</tr>
<tr>
<td valign="top">

PageSize



</td>
<td valign="top">

The page size of the database, in bytes.



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

PartnerState



</td>
<td valign="top">

Information about the database server's status in a mirroring configuration. Values include: *Connected*, when there is a connection from this server to a partner server and a connection from the partner server to this server; *Disconnected* when there are no connections between this server and the partner server; Incoming only when there is a there is a connection from the partner server to this server; and *Outgoing* only when there is a connection from this server to the partner server. The value is *NULL* when the database server is not involved in a mirroring configuration.



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

Prepares



</td>
<td valign="top">

The number of statement prepares performed for the database.



</td>
</tr>
<tr>
<td valign="top">

PrepStmt



</td>
<td valign="top">

The number of prepared statements currently being maintained by the database server for the current database.



</td>
</tr>
<tr>
<td valign="top">

PreviousTimelineID



</td>
<td valign="top">

For internal use only.



</td>
</tr>
<tr>
<td valign="top">

ProcedurePages



</td>
<td valign="top">

The number of relocatable heap pages that have been used for procedures.



</td>
</tr>
<tr>
<td valign="top">

ProcedureProfiling



</td>
<td valign="top">

Whether procedure profiling is turned on for the database.



</td>
</tr>
<tr>
<td valign="top">

PropertyHistoryList



</td>
<td valign="top">

The current set of properties being tracked for this database.



</td>
</tr>
<tr>
<td valign="top">

QueryBypassed



</td>
<td valign="top">

The number of requests reused from the plan cache.



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

The number of cached execution plans across all connections.



</td>
</tr>
<tr>
<td valign="top">

QueryCachePages



</td>
<td valign="top">

The number of pages used to cache execution plans.



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

The number of times a hash join was converted to a nested loops join.



</td>
</tr>
<tr>
<td valign="top">

QueryLowMemoryStrategy



</td>
<td valign="top">

The number of times the server changed its execution plan during execution as a result of low memory conditions. The strategy can change because less memory is available than the optimizer estimated, or because the execution plan required more memory than the optimizer estimated.



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

The number of reused query plans.



</td>
</tr>
<tr>
<td valign="top">

QueryRowsFetched



</td>
<td valign="top">

The number of rows that have been read from base tables, either by a sequential scan or an index scan, for this database.



</td>
</tr>
<tr>
<td valign="top">

QueryRowsMaterialized



</td>
<td valign="top">

The number of rows written to work tables during query processing.



</td>
</tr>
<tr>
<td valign="top">

ReadOnly



</td>
<td valign="top">

Whether the database is being run in read-only mode \(On\) or not \(Off\).



</td>
</tr>
<tr>
<td valign="top">

ReceivingTracingFrom



</td>
<td valign="top">

The name of the database from which the tracing data is coming. The value is a blank string if tracing is not attached.



</td>
</tr>
<tr>
<td valign="top">

RecoveryUrgency



</td>
<td valign="top">

An estimate of the amount of time required to recover the database as a percentage of the recovery time setting of the database.



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

The number of times recursive hash join used a nested loops strategy.



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

RelocatableHeapPages



</td>
<td valign="top">

The number of pages used for relocatable heaps \(cursors, statements, procedures, triggers, views, and so on.\).



</td>
</tr>
<tr>
<td valign="top">

RemoteTrunc



</td>
<td valign="top">

The minimal confirmed log offset for the SQL Remote Message Agent.



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

The number of times connections to the database waited for atomic access, or NULL if the -zt option was not specified.



</td>
</tr>
<tr>
<td valign="top">

ReqCountBlockIO



</td>
<td valign="top">

The number of times connections to the database waited for I/O to complete, or NULL if the -zt option was not specified.



</td>
</tr>
<tr>
<td valign="top">

ReqCountBlockLock



</td>
<td valign="top">

The number of times connections to the database waited for a lock, or NULL if the -zt option was not specified.



</td>
</tr>
<tr>
<td valign="top">

ReqCountUnscheduled



</td>
<td valign="top">

The number of times connections to the database waited for scheduling, or NULL if the -zt option was not specified.



</td>
</tr>
<tr>
<td valign="top">

ReqTimeActive



</td>
<td valign="top">

The amount of time spent in seconds processing requests, or NULL if the -zt option was not specified.



</td>
</tr>
<tr>
<td valign="top">

ReqTimeBlockContention



</td>
<td valign="top">

The amount of time spent in seconds waiting for atomic access, or NULL if the RequestTiming server property is set to Off.



</td>
</tr>
<tr>
<td valign="top">

ReqTimeBlockIO



</td>
<td valign="top">

The amount of time spent in seconds waiting for I/O to complete, or NULL if the -zt option was not specified.



</td>
</tr>
<tr>
<td valign="top">

ReqTimeBlockLock



</td>
<td valign="top">

The amount of time spent in seconds waiting for a lock, or NULL if the -zt option was not specified.



</td>
</tr>
<tr>
<td valign="top">

ReqTimeUnscheduled



</td>
<td valign="top">

The amount of unscheduled time, or NULL if the -zt option was not specified.



</td>
</tr>
<tr>
<td valign="top">

RequestsReceived



</td>
<td valign="top">

The number of client/server communication requests or round trips. This property is different from PacketsReceived in that multi-packet requests count as one request, and liveness packets are not included.



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

RollbackLogPages



</td>
<td valign="top">

The number of pages in the rollback log.



</td>
</tr>
<tr>
<td valign="top">

SendingTracingTo



</td>
<td valign="top">

The connection string where the tracing data is being sent. The value is a blank string if tracing is not attached.



</td>
</tr>
<tr>
<td valign="top">

SnapshotCount



</td>
<td valign="top">

The number of snapshots associated with the database.



</td>
</tr>
<tr>
<td valign="top">

SnapshotIsolationState



</td>
<td valign="top">

Whether snapshot isolation is enabled for the database \(On\) or not \(Off\), or whether it will be enabled \(in\_transition\_to\_on\) or disabled \(in\_transition\_to\_off \) once the current transactions complete.



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

The number of statements processed by the semantic query transformation phase, but which skipped some of the semantic transformations.



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

SynchronizationSchemaChangeActive



</td>
<td valign="top">

Whether an active connection executed a START SYNCHRONIZATION SCHEMA CHANGE statement but has not executed a STOP SYNCHRONIZATION SCHEMA CHANGE statement \(On\) or not \(Off\).



</td>
</tr>
<tr>
<td valign="top">

TempFileName



</td>
<td valign="top">

The file name of the database temporary file, including path.



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

TimelineBranchOffset



</td>
<td valign="top">

For internal use only.



</td>
</tr>
<tr>
<td valign="top">

TimeWithoutClientConnection



</td>
<td valign="top">

The time in seconds since the last command sequence or TDS client connection, or the time since the database started if no connections have been made to the database. The value is 0 if there is a current connection.



</td>
</tr>
<tr>
<td valign="top">

TimeZone



</td>
<td valign="top">

The time zone that the database uses for time zone calculations. The value is NULL if the Timezone database option is not set.



</td>
</tr>
<tr>
<td valign="top">

TriggerPages



</td>
<td valign="top">

The number of relocatable heap pages used for triggers.



</td>
</tr>
<tr>
<td valign="top">

UTCTimestampCatalog



</td>
<td valign="top">

Whether the database is storing UTC timestamps in the system tables \(On\) or not \(Off\).



</td>
</tr>
<tr>
<td valign="top">

VersionStorePages



</td>
<td valign="top">

The number of pages in the temporary file that are being used for the row version store when snapshot isolation is enabled.



</td>
</tr>
<tr>
<td valign="top">

ViewPages



</td>
<td valign="top">

The number of relocatable heap pages used for views.



</td>
</tr>
<tr>
<td valign="top">

WriteChecksum



</td>
<td valign="top">

Whether the database server adds checksums to pages before they are written out \(On\) or not \(Off\).



</td>
</tr>
<tr>
<td valign="top">

XPathCompiles



</td>
<td valign="top">

The number of times any XPath query \(using the OPENXML operator\) was compiled by the database server since database server startup.



</td>
</tr>
</table>

