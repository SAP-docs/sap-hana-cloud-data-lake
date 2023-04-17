<!-- loio3c0dc9266c5f1014ab64f98d66d5674e -->

# SABulkCopyColumnMapping\(string, int\) Constructor

Creates a new column mapping, using a column name to refer to the source column and a column ordinal to refer to the destination column.



Visual Basic
:   ```
Public Sub SABulkCopyColumnMapping (
    ByVal sourceColumn As String,
    ByVal destinationColumnOrdinal As Integer
)
```

C\#
:   ```
public SABulkCopyColumnMapping (
    string sourceColumn,
    int destinationColumnOrdinal
)
```



## Parameters

sourceColumn
:   The name of the source column within the data source.

destinationColumnOrdinal
:   The ordinal position of the destination column within the destination table. The first column in a table has ordinal position zero.

