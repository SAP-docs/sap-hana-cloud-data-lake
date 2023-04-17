<!-- loio3bd0bbcf6c5f1014ba59adc0772943b4 -->

# Server-side Data Access Using JDBC

Database transaction logic implemented as Java methods that can be called from SQL can offer significant advantages over traditional SQL stored procedures.

The interface to a Java method is implemented using specialized SQL stored procedure definition syntax. Calls to Java methods, including those that use JDBC, closely parallel calls to SQL stored procedures that are comprised entirely of SQL statements. Although the following topics demonstrate how to use JDBC from the database \(server-side JDBC\), the examples also demonstrate how to write JDBC for a client-side application.

As with other programming interfaces, SQL statements in JDBC can be either **static** or **dynamic**. Static SQL statements are constructed in the Java application and sent to the database. The database server parses the statement, selects an execution plan, and executes the statement.

If the same or similar SQL statement is executed many times \(many inserts into one table, for example\), there can be significant overhead when using static SQL because the statement preparation step has to be executed each time.

In contrast, a dynamic SQL statement contains place holders. The statement, prepared once using these place holders, can be executed many times without the additional expense of preparing it each time.

The following topics provide examples of both static and dynamic SQL statement execution as well as execution of batches \(wide inserts, deletes, updates, and merges\).

