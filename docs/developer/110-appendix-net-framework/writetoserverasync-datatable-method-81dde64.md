<!-- loio81dde64d6ce21014a052c1863c8c7823 -->

# WriteToServerAsync\(DataTable\) Method

Copies all rows in the supplied System.Data.DataTable to a destination table specified by the SABulkCopy.DestinationTableName property of the SABulkCopy object.



Visual Basic
:   ```
Public Function WriteToServerAsync (ByVal table As DataTable) As Task
```

C\#
:   ```
public Task WriteToServerAsync (DataTable table)
```



## Parameters

table
:   A System.Data.DataTable whose rows are copied to the destination table.

