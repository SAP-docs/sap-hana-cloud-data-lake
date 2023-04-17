<!-- loio3bd05f3c6c5f101497b7e1acc5dcd6ef -->

# .NET Connection Pooling

The SQL Anywhere .NET Data Provider supports native .NET connection pooling. Connection pooling allows your application to reuse existing connections by saving the connection handle to a pool so it can be reused, rather than repeatedly creating a new connection to the database.

Connection pooling is enabled and disabled using the *Pooling* connection parameter. Connection pooling is enabled by default.

The maximum pool size is set in your connection string using the *Max Pool Size* parameter. The minimum or initial pool size is set in your connection string using the *Min Pool Size* parameter. The default maximum pool size is 100, while the default minimum pool size is 0.

The following is an example of a .NET connection string. Data source names are supported.

```
"Data Source=SAP IQ 17 Demo;Pooling=true;Max Pool Size=50;Min Pool Size=5;Password="+pwd
```

Do not use the ConnectionPool \(CPOOL\) connection parameter to enable or disable .NET connection pooling. Use the Pooling connection parameter for this purpose.

When your application first attempts to connect to the database, it checks the pool for an existing connection that uses the same connection parameters you have specified. If a matching connection is found, that connection is used. Otherwise, a new connection is used. When you disconnect, the connection is returned to the pool so that it can be reused.

Multiple connection pools are supported by .NET and a different connection string creates a different pool. To reuse a pooled connection, the connection strings must be textually identical. For .NET applications, the following two connection strings are not considered equivalent for connection pooling; thus each string would create its own connection pool.

```
UID=HDLADMIN;PWD=passwd;ConnectionName=One
UserID=HDLADMIN;PWD=passwd;ConnectionName=One
```

If Min Pool Size=5, then 5 connections are made to the database server at the time the first connection is made. The next 4 concurrent connections will come out of this pool. Any additional concurrent connections are added as needed. This option is useful for multithreaded applications that make several connections where you want a quick response to an "open" request \(the speed is equivalent to unpooling a pooled connection\).

If Max Pool Size=20, then up to 20 concurrent connections will be pooled when closed. Any concurrent connections beyond the first 20 closed connections will not be pooled \(that is, at most 20 connections will be pooled and the rest will be closed\). Note each pooled connection counts as a "real" connection to the database server. Max Pool Size does not prevent the application from making as many concurrent connections as it desires.

A .NET application that makes at most one connection to the database server at a time will not need to adjust the Min and Max pool size settings.

Connection pooling is not supported for non-standard database authentication such as Integrated or Kerberos logins. Only user ID and password authentication is supported.

The database server also supports connection pooling. This feature is controlled using the ConnectionPool \(CPOOL\) connection parameter. However, the .NET Data Provider does not use this server feature and disables it \(CPOOL=NO\). All connection pooling is done in the .NET client application instead \(client-side connection pooling\).

