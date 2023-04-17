<!-- loio81de02096ce21014a9c6a7b3ceb26b29 -->

# WriteToServerAsync\(DataTable, DataRowState, CancellationToken\) Method

Copies only rows that match the supplied row state in the supplied System.Data.DataTable to a destination table specified by the SABulkCopy.DestinationTableName property of the SABulkCopy object.The cancellation token can be used to request that the operation be abandoned before the command timeout elapses.



Visual Basic
:   ```
Public Function WriteToServerAsync (
    ByVal table As DataTable,
    ByVal rowState As DataRowState,
    ByVal cancellationToken As CancellationToken
) As Task
```

C\#
:   ```
public Task WriteToServerAsync (
    DataTable table,
    DataRowState rowState,
    CancellationToken cancellationToken
)
```



## Parameters

table
:   A System.Data.DataTable whose rows are copied to the destination table.

rowState
:   A value from the System.Data.DataRowState enumeration. Only rows matching the row state are copied to the destination.

cancellationToken
:   The cancellation instruction. A P:System.Threading.CancellationToken.None value in this parameter makes this method equivalent to SABulkCopy.WriteToServerAsync\(System.Data.DataTable, System.Data.DataRowState\).



## Returns

A task representing the asynchronous operation.



## Exceptions

SAException class
:   Returned in the task object, any error returned by SQL Server that occurred while copying data.



## Remarks

Exceptions are reported via the returned Task object.

