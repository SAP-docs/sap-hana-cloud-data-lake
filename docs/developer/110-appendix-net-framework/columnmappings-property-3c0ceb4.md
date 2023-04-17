<!-- loio3c0ceb4b6c5f1014bf9fbc2fb5a756cd -->

# ColumnMappings Property

Returns a collection of SABulkCopyColumnMapping items.



Visual Basic
:   ```
Public ReadOnly Property ColumnMappings As SABulkCopyColumnMappingCollection
```

C\#
:   ```
public SABulkCopyColumnMappingCollection ColumnMappings {get;}
```



## Remarks

Column mappings define the relationships between columns in the data source and columns in the destination.

By default, it is an empty collection.

The property cannot be modified while WriteToServer is executing.

If ColumnMappings is empty when WriteToServer is executed, then the first column in the source is mapped to the first column in the destination, the second to the second, and so on. This behavior takes place as long as the column types are convertible, there are at least as many destination columns as source columns, and any extra destination columns are nullable.

