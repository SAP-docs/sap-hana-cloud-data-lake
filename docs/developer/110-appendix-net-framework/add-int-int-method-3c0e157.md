<!-- loio3c0e15796c5f101482dbbc9c707db822 -->

# Add\(int, int\) Method

Creates a new SABulkCopyColumnMapping object using ordinals to specify both source and destination columns, and adds the mapping to the collection.



Visual Basic
:   ```
Public Function Add (
    ByVal sourceColumnOrdinal As Integer,
    ByVal destinationColumnOrdinal As Integer
) As SABulkCopyColumnMapping
```

C\#
:   ```
public SABulkCopyColumnMapping Add (
    int sourceColumnOrdinal,
    int destinationColumnOrdinal
)
```



## Parameters

sourceColumnOrdinal
:   The ordinal position of the source column within the data source.

destinationColumnOrdinal
:   The ordinal position of the destination column within the destination table.

