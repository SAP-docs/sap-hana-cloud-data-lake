<!-- loio81de0b7e6ce210148656edb213ed8d6b -->

# WriteToServerAsync\(IDataReader\) Method

Copies all rows in the supplied System.Data.IDataReader to a destination table specified by the SABulkCopy.DestinationTableName property of the SABulkCopy object.



Visual Basic
:   ```
Public Function WriteToServerAsync (ByVal reader As IDataReader) As Task
```

C\#
:   ```
public Task WriteToServerAsync (IDataReader reader)
```



## Parameters

reader
:   A System.Data.IDataReader whose rows are copied to the destination table.

