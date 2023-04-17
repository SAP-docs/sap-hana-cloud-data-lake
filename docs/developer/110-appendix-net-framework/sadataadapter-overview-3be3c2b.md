<!-- loio3be3c2bc6c5f1014819f86953d2022c9 -->

# SADataAdapter: Overview

The SADataAdapter retrieves a result set into a DataTable. A DataSet is a collection of tables \(DataTables\) and the relationships and constraints between those tables. The DataSet is built into the .NET Framework, and is independent of the Data Provider used to connect to your database.

When you use the SADataAdapter, you must be connected to the database to fill a DataTable and to update the database with changes made to the DataTable. However, once the DataTable is filled, you can modify the DataTable while disconnected from the database.

If you do not want to apply your changes to the database right away, you can write the DataSet, including the data and/or the schema, to an XML file using the WriteXml method. Then, you can apply the changes at a later time by loading a DataSet with the ReadXml method. The following shows two examples.

```
ds.WriteXml("Employees.xml");
ds.WriteXml("EmployeesWithSchema.xml", XmlWriteMode.WriteSchema);
```

For more information, see the .NET Framework documentation for WriteXml and ReadXml.

When you call the Update method to apply changes from the DataSet to the database, the SADataAdapter analyzes the changes that have been made and then invokes the appropriate statements, INSERT, UPDATE, or DELETE, as necessary. When you use the DataSet, you can only make changes \(inserts, updates, or deletes\) to data that is from a single table. You cannot update result sets that are based on joins. If another user has a lock on the row you are trying to update, an exception is thrown.

> ### Caution:  
> Any changes you make to the DataSet are made while you are disconnected. Your application does not have locks on these rows in the database. Your application must be designed to resolve any conflicts that may occur when changes from the DataSet are applied to the database if another user changes the data you are modifying before your changes are applied to the database.



## Resolving Conflicts when Using the SADataAdapter

When you use the SADataAdapter, no locks are placed on the rows in the database. This means there is the potential for conflicts to arise when you apply changes from the DataSet to the database. Your application should include logic to resolve or log conflicts that arise.

Some of the conflicts that your application logic should address include:

Unique primary keys
:   If two users insert new rows into a table, each row must have a unique primary key. For tables with AUTOINCREMENT primary keys, the values in the DataSet may become out of sync with the values in the data source.

    It is possible to obtain the values for AUTOINCREMENT primary keys for newly inserted rows.

Updates made to the same value
:   If two users modify the same value, your application should include logic to determine which value is correct.

Schema changes
:   If a user modifies the schema of a table you have updated in the DataSet, the update will fail when you apply the changes to the database.

Data concurrency
:   Concurrent applications should see a consistent set of data. The SADataAdapter does not place a lock on rows that it fetches, so another user can update a value in the database once you have retrieved the DataSet and are working offline.

Many of these potential problems can be avoided by using the SACommand, SADataReader, and SATransaction objects to apply changes to the database. The SATransaction object is recommended because it allows you to set the isolation level for the transaction and it places locks on the rows so that other users cannot modify them.

To simplify the process of conflict resolution, you can design your INSERT, UPDATE, or DELETE statement to be a stored procedure call. By including INSERT, UPDATE, and DELETE statements in stored procedures, you can catch the error if the operation fails. In addition to the statement, you can add error handling logic to the stored procedure so that if the operation fails the appropriate action is taken, such as recording the error to a log file, or trying the operation again.

