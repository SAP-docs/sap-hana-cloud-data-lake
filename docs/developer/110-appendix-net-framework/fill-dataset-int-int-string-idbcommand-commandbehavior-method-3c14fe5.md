<!-- loio3c14fe506c5f1014b3a9bc3cb3b42a2b -->

# Fill\(DataSet, int, int, string, IDbCommand, CommandBehavior\) Method

Adds or refreshes rows in a System.Data.DataSet or System.Data.DataTable object with data from the database.



Visual Basic
:   ```
Protected Overrides Function Fill (
    ByVal dataSet As DataSet,
    ByVal startRecord As Integer,
    ByVal maxRecords As Integer,
    ByVal srcTable As String,
    ByVal command As IDbCommand,
    ByVal behavior As CommandBehavior
) As Integer
```

C\#
:   ```
protected override int Fill (
    DataSet dataSet,
    int startRecord,
    int maxRecords,
    string srcTable,
    IDbCommand command,
    CommandBehavior behavior
)
```



## Parameters

dataSet
:   A System.Data.DataSet to fill with records and optionally, schema.

startRecord
:   The zero-based record number with which to start.

maxRecords
:   The maximum number of records to be read into the System.Data.DataSet.

srcTable
:   The name of the source table to use for table mapping.

command
:   The SQL SELECT statement used to retrieve rows from the data source.

behavior
:   One of the CommandBehavior values.



## Returns

The number of rows successfully added or refreshed in the System.Data.DataSet.



## Remarks

Even if you use the startRecord argument to limit the number of records that are copied to the DataSet, all records in the SADataAdapter query are fetched from the database to the client. For large result sets, this can have a significant performance impact.

An alternative is to use an SADataReader when a read-only, forward-only result set is sufficient, perhaps with SQL statements \(ExecuteNonQuery\) to undertake modifications. Another alternative is to write a stored procedure that returns only the result you need.

If SelectCommand does not return any rows, then no tables are added to the DataSet and no exception is raised.

For more information, see "Data access and manipulation".

