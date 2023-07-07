<!-- loioa4cadebce370468184c1287e5a8b6464 -->

# Database Server Property Tracking

The database server can store the values of numeric database server properties so that you can track the changes of numeric database server properties over time.

Tracking database server property values over time aids in evaluating the overall health of a database server. For example, a brief increase in CPU usage may not be an issue, but if the CPU usage is at 100 percent for an extended period of time, it could indicate that the hardware is insufficient.

Rather than having to poll, analyze, and store database server property values at regular intervals, configure the database server to track database server properties that return numeric values. These values are stored in memory for a period of time so that polling can be done at larger intervals, reducing the load on the database server.

When database server property tracking is enabled, property values are tracked at fixed intervals and you can query historic property values by using the sp\_property\_history system procedure.

