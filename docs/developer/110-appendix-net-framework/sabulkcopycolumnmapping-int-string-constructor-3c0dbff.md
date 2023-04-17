<!-- loio3c0dbff66c5f1014892af01252246747 -->

# SABulkCopyColumnMapping\(int, string\) Constructor

Creates a new column mapping, using a column ordinal to refer to the source column and a column name to refer to the destination column.



Visual Basic
:   ```
Public Sub SABulkCopyColumnMapping (
    ByVal sourceColumnOrdinal As Integer,
    ByVal destinationColumn As String
)
```

C\#
:   ```
public SABulkCopyColumnMapping (
    int sourceColumnOrdinal,
    string destinationColumn
)
```



## Parameters

sourceColumnOrdinal
:   The ordinal position of the source column within the data source. The first column in a data source has ordinal position zero.

destinationColumn
:   The name of the destination column within the destination table.

