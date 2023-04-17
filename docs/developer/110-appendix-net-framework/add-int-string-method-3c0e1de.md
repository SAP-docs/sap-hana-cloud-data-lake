<!-- loio3c0e1de06c5f10148c71ed09a6aa5859 -->

# Add\(int, string\) Method

Creates a new SABulkCopyColumnMapping object using a column ordinal to refer to the source column and a column name to refer to the destination column, and adds mapping to the collection.



Visual Basic
:   ```
Public Function Add (
    ByVal sourceColumnOrdinal As Integer,
    ByVal destinationColumn As String
) As SABulkCopyColumnMapping
```

C\#
:   ```
public SABulkCopyColumnMapping Add (
    int sourceColumnOrdinal,
    string destinationColumn
)
```



## Parameters

sourceColumnOrdinal
:   The ordinal position of the source column within the data source.

destinationColumn
:   The name of the destination column within the destination table.

