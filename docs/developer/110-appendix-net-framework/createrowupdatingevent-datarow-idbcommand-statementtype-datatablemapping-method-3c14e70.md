<!-- loio3c14e7096c5f1014bbcbd63d5a52dfea -->

# CreateRowUpdatingEvent\(DataRow, IDbCommand, StatementType, DataTableMapping\) Method

Initializes a new instance of the System.Data.Common.RowUpdatingEventArgs class.



Visual Basic
:   ```
Protected Overrides Function CreateRowUpdatingEvent (
    ByVal dataRow As DataRow,
    ByVal command As IDbCommand,
    ByVal statementType As StatementType,
    ByVal tableMapping As DataTableMapping
) As RowUpdatingEventArgs
```

C\#
:   ```
protected override RowUpdatingEventArgs CreateRowUpdatingEvent (
    DataRow dataRow,
    IDbCommand command,
    StatementType statementType,
    DataTableMapping tableMapping
)
```



## Parameters

dataRow
:   The System.Data.DataRow used to update the data source.

command
:   The System.Data.IDbCommand executed during the System.Data.IDataAdapter.Update\(System.Data.DataSet\).

statementType
:   Whether the command is an UPDATE, INSERT, DELETE, or SELECT statement.

tableMapping
:   A System.Data.Common.DataTableMapping object.



## Returns

A new instance of the System.Data.Common.RowUpdatingEventArgs class.

