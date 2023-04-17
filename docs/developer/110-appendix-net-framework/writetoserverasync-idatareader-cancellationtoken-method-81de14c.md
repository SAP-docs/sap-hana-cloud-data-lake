<!-- loio81de14c46ce21014a73cfd08ca31b321 -->

# WriteToServerAsync\(IDataReader, CancellationToken\) Method

Copies all rows in the supplied System.Data.IDataReader to a destination table specified by the SAClient.SqlBulkCopy.DestinationTableName property of the SAClient.SqlBulkCopy object.The cancellation token can be used to request that the operation be abandoned before the command timeout elapses.



Visual Basic
:   ```
Public Function WriteToServerAsync (
    ByVal reader As IDataReader,
    ByVal cancellationToken As CancellationToken
) As Task
```

C\#
:   ```
public Task WriteToServerAsync (
    IDataReader reader,
    CancellationToken cancellationToken
)
```



## Parameters

reader
:   A System.Data.IDataReader whose rows are copied to the destination table.

cancellationToken
:   The cancellation instruction. A P:System.Threading.CancellationToken.None value in this parameter makes this method equivalent to SABulkCopy.WriteToServerAsync\(System.Data.IDataReader\).



## Returns

A task representing the asynchronous operation.



## Exceptions

SAException class
:   Returned in the task object, any error returned by SQL Server that occurred while copying data.



## Remarks

Exceptions are reported via the returned Task object.

