<!-- loio81dddcda6ce2101490588b871da8e6f3 -->

# WriteToServerAsync\(DataRow\[\], CancellationToken\) Method

Copies all rows from the supplied System.Data.DataRow array to a destination table specified by the SABulkCopy.DestinationTableName property of the SABulkCopy object.



Visual Basic
:   ```
Public Function WriteToServerAsync (
    ByVal rows As DataRow(),
    ByVal cancellationToken As CancellationToken
) As Task
```

C\#
:   ```
public Task WriteToServerAsync (
    DataRow[] rows,
    CancellationToken cancellationToken
)
```



## Parameters

rows
:   An array of System.Data.DataRow objects that are copied to the destination table.

cancellationToken
:   The cancellation instruction. A P:System.Threading.CancellationToken.None value in this parameter makes this method equivalent to SABulkCopy.WriteToServerAsync\(System.Data.DataTable\).



## Returns

A task representing the asynchronous operation.



## Exceptions

SAException class
:   Returned in the task object, any error returned by the database server that occurred while copying data.



## Remarks

The cancellation token can be used to request that the operation be abandoned before the command timeout elapses. Exceptions are reported via the returned Task object.

