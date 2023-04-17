<!-- loio3c0db75a6c5f10148196b0e7ff53b7b9 -->

# SABulkCopyColumnMapping\(int, int\) Constructor

Creates a new column mapping, using column ordinals to refer to source and destination columns.



Visual Basic
:   ```
Public Sub SABulkCopyColumnMapping (
    ByVal sourceColumnOrdinal As Integer,
    ByVal destinationColumnOrdinal As Integer
)
```

C\#
:   ```
public SABulkCopyColumnMapping (
    int sourceColumnOrdinal,
    int destinationColumnOrdinal
)
```



## Parameters

sourceColumnOrdinal
:   The ordinal position of the source column within the data source. The first column in a data source has ordinal position zero.

destinationColumnOrdinal
:   The ordinal position of the destination column within the destination table. The first column in a table has ordinal position zero.

