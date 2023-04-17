<!-- loio3c15e0696c5f1014a800bda657688d96 -->

# Update\(DataRow\[\], DataTableMapping\) Method

Updates the tables in a database with the changes made to the DataSet.



Visual Basic
:   ```
Protected Overrides Function Update (
    ByVal dataRows As DataRow(),
    ByVal tableMapping As DataTableMapping
) As Integer
```

C\#
:   ```
protected override int Update (
    DataRow[] dataRows,
    DataTableMapping tableMapping
)
```



## Parameters

dataRows
:   An array of System.Data.DataRow to update from.

tableMapping
:   The System.Data.IDataAdapter.TableMappings collection to use.



## Returns

The number of rows successfully updated from the System.Data.DataRow array.



## Remarks

The Update is carried out using the InsertCommand, UpdateCommand, and DeleteCommand on each row in the data set that has been inserted, updated, or deleted.

For more information, see "Data access and manipulation".

**Related Information**  


[DeleteCommand Property](deletecommand-property-3c14eed.md "Specifies an SACommand object that is executed against the database when the Update method is called to delete rows in the database that correspond to deleted rows in the DataSet.")

[InsertCommand Property](insertcommand-property-3c1559a.md "Specifies an SACommand that is executed against the database when the Update method is called that adds rows to the database to correspond to rows that were inserted in the DataSet.")

[UpdateCommand Property](updatecommand-property-3c15f10.md "Specifies an SACommand that is executed against the database when the Update method is called to update rows in the database that correspond to updated rows in the DataSet.")

