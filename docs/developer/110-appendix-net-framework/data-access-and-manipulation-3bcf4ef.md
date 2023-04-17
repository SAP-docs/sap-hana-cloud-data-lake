<!-- loio3bcf4ef66c5f1014abecbc93e5669d28 -->

# Data Access and Manipulation

With the data lake Relational Engine .NET Data Provider, there are two ways you can access data, using the SACommand class or the SADataAdapter class.

 SACommand object
 :   The SACommand object is the recommended way of accessing and manipulating data in .NET.

    The SACommand object allows you to execute SQL statements that retrieve or modify data directly from the database. Using the SACommand object, you can issue SQL statements and call stored procedures directly against the database.

    Within an SACommand object, an SADataReader is used to return read-only result sets from a query or stored procedure. The SADataReader returns only one row at a time, but this does not degrade performance because the client-side libraries use prefetch buffering to prefetch several rows at a time.

    Using the SACommand object allows you to group your changes into transactions rather than operating in autocommit mode. When you use the SATransaction object, locks are placed on the rows so that other users cannot modify them.

  SADataAdapter object
 :   The SADataAdapter object retrieves the entire result set into a DataSet. A DataSet is a disconnected store for data that is retrieved from a database. You can then edit the data in the DataSet and when you are finished, the SADataAdapter object updates the database with the changes made to the DataSet. When you use the SADataAdapter, there is no way to prevent other users from modifying the rows in your DataSet. You must include logic within your application to resolve any conflicts that may occur.

 There is no performance impact from using the SADataReader within an SACommand object to fetch rows from the database rather than the SADataAdapter object.

