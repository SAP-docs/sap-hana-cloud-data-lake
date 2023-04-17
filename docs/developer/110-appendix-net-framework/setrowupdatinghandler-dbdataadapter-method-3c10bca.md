<!-- loio3c10bca46c5f1014862dd3beb85211bf -->

# SetRowUpdatingHandler\(DbDataAdapter\) Method

Registers the SACommandBuilder object to handle the SADataAdapter.RowUpdating event for an SADataAdapter object.



Visual Basic
:   ```
Protected Overrides Sub SetRowUpdatingHandler (ByVal adapter As DbDataAdapter)
```

C\#
:   ```
protected override void SetRowUpdatingHandler (DbDataAdapter adapter)
```



## Parameters

adapter
:   The SADataAdapter object to be used for the update.

**Related Information**  


[SACommandBuilder Class](sacommandbuilder-class-3c10cc1.md "A way to generate single-table SQL statements that reconcile changes made to a DataSet with the data in the associated database.")

[SADataAdapter Class](sadataadapter-class-3c15f91.md "Represents a set of commands and a database connection used to fill a System.Data.DataSet and to update a database.")

[RowUpdating Event](rowupdating-event-3c1585a.md "Occurs during an update before a command is executed against the data source.")

