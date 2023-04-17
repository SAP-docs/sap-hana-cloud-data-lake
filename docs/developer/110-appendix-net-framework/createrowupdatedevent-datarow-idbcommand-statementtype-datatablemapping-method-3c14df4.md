<!-- loio3c14df476c5f1014adb9bd3622f178f1 -->

# CreateRowUpdatedEvent\(DataRow, IDbCommand, StatementType, DataTableMapping\) Method

Initializes a new instance of the System.Data.Common.RowUpdatedEventArgs class.



Visual Basic
:   ```
Protected Overrides Function CreateRowUpdatedEvent (
    ByVal dataRow As DataRow,
    ByVal command As IDbCommand,
    ByVal statementType As StatementType,
    ByVal tableMapping As DataTableMapping
) As RowUpdatedEventArgs
```

C\#
:   ```
protected override RowUpdatedEventArgs CreateRowUpdatedEvent (
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

A new instance of the System.Data.Common.RowUpdatedEventArgs class.

