<!-- loio81ddd2b46ce21014a0efc391034c0502 -->

# WriteToServerAsync\(DataRow\[\]\) Method

Copies all rows from the supplied System.Data.DataRow array to a destination table specified by the SABulkCopy.DestinationTableName property of the SABulkCopy object.



Visual Basic
:   ```
Public Function WriteToServerAsync (ByVal rows As DataRow()) As Task
```

C\#
:   ```
public Task WriteToServerAsync (DataRow[] rows)
```



## Parameters

rows
:   An array of System.Data.DataRow objects that are copied to the destination table.

