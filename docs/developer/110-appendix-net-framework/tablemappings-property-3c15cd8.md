<!-- loio3c15cd8f6c5f10149705a8345507e842 -->

# TableMappings Property

Specifies a collection that provides the master mapping between a source table and a DataTable.



Visual Basic
:   ```
Public ReadOnly Shadows Property TableMappings As DataTableMappingCollection
```

C\#
:   ```
public new DataTableMappingCollection TableMappings {get;}
```



## Remarks

The default value is an empty collection.

When reconciling changes, the SADataAdapter uses the DataTableMappingCollection collection to associate the column names used by the data source with the column names used by the DataSet.

