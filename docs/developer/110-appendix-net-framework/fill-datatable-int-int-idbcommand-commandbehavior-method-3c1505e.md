<!-- loio3c1505e76c5f1014b4a5adb385bb5a58 -->

# Fill\(DataTable\[\], int, int, IDbCommand, CommandBehavior\) Method

Adds or refreshes rows in a specified range in the System.Data.DataSet to match those in the data source using the System.Data.DataSet and System.Data.DataTable names.



Visual Basic
:   ```
Protected Overrides Function Fill (
    ByVal dataTables As DataTable(),
    ByVal startRecord As Integer,
    ByVal maxRecords As Integer,
    ByVal command As IDbCommand,
    ByVal behavior As CommandBehavior
) As Integer
```

C\#
:   ```
protected override int Fill (
    DataTable[] dataTables,
    int startRecord,
    int maxRecords,
    IDbCommand command,
    CommandBehavior behavior
)
```



## Parameters

dataTables
:   The System.Data.DataTable objects to fill from the data source.

startRecord
:   The zero-based record number to start with.

maxRecords
:   The maximum number of records to retrieve.

command
:   The System.Data.IDbCommand executed to fill the System.Data.DataTable objects.

behavior
:   One of the System.Data.CommandBehavior values.



## Returns

The number of rows added to or refreshed in the data tables.



## Remarks

Even if you use the startRecord argument to limit the number of records that are copied to the DataSet, all records in the SADataAdapter query are fetched from the database to the client. For large result sets, this can have a significant performance impact.

An alternative is to use an SADataReader when a read-only, forward-only result set is sufficient, perhaps with SQL statements \(ExecuteNonQuery\) to undertake modifications. Another alternative is to write a stored procedure that returns only the result you need.

If SelectCommand does not return any rows, then no tables are added to the DataSet and no exception is raised.

For more information, see "Data access and manipulation".

