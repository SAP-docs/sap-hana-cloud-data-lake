<!-- loio3c0e259a6c5f10149899ce7b57ec78cc -->

# Add\(string, int\) Method

Creates a new SABulkCopyColumnMapping object using a column name to refer to the source column and a column ordinal to refer to the destination the column, and adds the mapping to the collection.



Visual Basic
:   ```
Public Function Add (
    ByVal sourceColumn As String,
    ByVal destinationColumnOrdinal As Integer
) As SABulkCopyColumnMapping
```

C\#
:   ```
public SABulkCopyColumnMapping Add (
    string sourceColumn,
    int destinationColumnOrdinal
)
```



## Parameters

sourceColumn
:   The name of the source column within the data source.

destinationColumnOrdinal
:   The ordinal position of the destination column within the destination table.



## Remarks

Creates a new column mapping, using column ordinals or names to refer to source and destination columns.

