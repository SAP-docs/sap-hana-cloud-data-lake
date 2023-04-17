<!-- loio81ddef596ce2101490f5bf9a471b1f46 -->

# WriteToServerAsync\(DataTable, CancellationToken\) Method

Copies only rows in the supplied System.Data.DataTable to a destination table specified by the SABulkCopy.DestinationTableName property of the SABulkCopy object.The cancellation token can be used to request that the operation be abandoned before the command timeout elapses.



Visual Basic
:   ```
Public Function WriteToServerAsync (
    ByVal table As DataTable,
    ByVal cancellationToken As CancellationToken
) As Task
```

C\#
:   ```
public Task WriteToServerAsync (
    DataTable table,
    CancellationToken cancellationToken
)
```



## Parameters

table
:   A System.Data.DataTable whose rows are copied to the destination table.

cancellationToken
:   The cancellation instruction. A P:System.Threading.CancellationToken.None value in this parameter makes this method equivalent to SABulkCopy.WriteToServerAsync\(System.Data.DataTable\).



## Returns

A task representing the asynchronous operation.



## Exceptions

SAException class
:   Returned in the task object, any error returned by SQL Server that occurred while copying data.



## Remarks

Exceptions are reported via the returned Task object.

