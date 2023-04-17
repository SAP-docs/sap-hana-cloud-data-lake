<!-- loiod95025a00e764e5fb2fa3f57f57d29ef -->

# Node.js Connection Pooling

The Node.js driver supports connection pooling. Connection pooling allows your application to reuse existing connections by automatically saving the connection to a pool so it can be reused, rather than repeatedly creating a new connection to data lake Relational Engine.

Connection pooling is enabled and disabled by using the `pooling` connection property. By default, connection pooling is disabled and must be enabled by specifying `pooling` to TRUE.

The maximum pool size for a specific connection string or option is set by using the `maxPoolSize` connection property. The `maxPoolSize` default value is 0, meaning that there is no limit.

The global maximum pool size is set by using the `setConnectionPoolLimit(Integer)` function. The default value of 0 does not set a limit on the number of connections in the connection pool.

When your application first attempts to connect to data lake Relational Engine, it checks the pool for an existing connection that uses the same connection properties you specified. If a matching connection is found, then that connection is used. Otherwise, a new connection is used. When you disconnect, the connection is returned to the pool so that it can be reused.

If `poolingCheck` is set to TRUE, the Node.js driver specifies that connections in the connection pool should be tested for viability before being reused. Connection viability is tested on all physical connections with the dummy SQL statement `SELECT 'ping' FROM DUMMY`. Connections deemed viable will be reused; connections deemed not viable will not be used and will be removed from the connection pool.

