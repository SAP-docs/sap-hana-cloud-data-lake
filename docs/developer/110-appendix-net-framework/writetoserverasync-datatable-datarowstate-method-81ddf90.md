<!-- loio81ddf9056ce21014abc99717a2326985 -->

# WriteToServerAsync\(DataTable, DataRowState\) Method

Copies only rows that match the supplied row state in the supplied System.Data.DataTable to a destination table specified by the SABulkCopy.DestinationTableName property of the SABulkCopy object.



Visual Basic
:   ```
Public Function WriteToServerAsync (
    ByVal table As DataTable,
    ByVal rowState As DataRowState
) As Task
```

C\#
:   ```
public Task WriteToServerAsync (
    DataTable table,
    DataRowState rowState
)
```



## Parameters

table
:   A System.Data.DataTable whose rows are copied to the destination table.

rowState
:   A value from the System.Data.DataRowState enumeration. Only rows matching the row state are copied to the destination.

