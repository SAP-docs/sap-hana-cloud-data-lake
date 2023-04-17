<!-- loio3c0d5bf36c5f101486df816db69fddcd -->

# WriteToServer\(DataTable, DataRowState\) Method

Copies all rows in the supplied System.Data.DataTable with the specified row state to a destination table specified by the DestinationTableName property of the SABulkCopy object.



Visual Basic
:   ```
Public Sub WriteToServer (
    ByVal table As DataTable,
    ByVal rowState As DataRowState
)
```

C\#
:   ```
public void WriteToServer (
    DataTable table,
    DataRowState rowState
)
```



## Parameters

table
:   A System.Data.DataTable whose rows are copied to the destination table.

rowState
:   A value from the System.Data.DataRowState enumeration. Only rows matching the row state are copied to the destination.



## Remarks

Only those rows matching the row state are copied.

**Related Information**  


[DestinationTableName Property](destinationtablename-property-3c0cf31.md "Gets or sets the name of the destination table on the database server.")

