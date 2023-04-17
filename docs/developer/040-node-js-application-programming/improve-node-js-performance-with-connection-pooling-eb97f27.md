<!-- loioeb97f27d17fe4013a7f5365dc16fd66f -->

# Improve Node.js Performance with Connection Pooling

Connection pooling can improve Node.js performance if the driver is making multiple, brief connections to the database server.



If connection pooling is enabled for a connection, when it is disconnected, the connection is automatically cached and may be reused when the application reconnects. When an application opens a new pooled connection, Node.js always searches the connection pool for an available connection with same connection string.

For connection pooling, use the `pooling` connection property. Node.js cleans up and reinitializes pooled connections.

To specify a maximum number of seconds that a connection can be cached in the pool, use the `connectionLifetime` connection property. A value of 0, which is the default, means that the connection is cached permanently.

If the application process connects again and there are cached connections available for the same connection string, then the cached connection is reused.

To ensure that connection pooling is transparent to the application, a connection is disconnected if a failure occurs when caching a connection.

If the lifetime of the connection has exceeded the specified connection lifetime, then the driver closes the connection. The connection is reinitialized, and the cached connection continues to be connected to the database server even though the application has disconnected it. The cleanup and reinitialization of a connection includes rolling back all outstanding transactions, isolations levels, locations, and the schema. Temporary objects, such as temporary tables and procedures, are not reset when a cached connection is reused.

