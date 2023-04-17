<!-- loio3c1e1f4e6c5f1014838cfe2ec9b1125d -->

# SARowUpdatedEventArgs\(DataRow, IDbCommand, StatementType, DataTableMapping\) Constructor

Initializes a new instance of the SARowUpdatedEventArgs class.



Visual Basic
:   ```
Public Sub SARowUpdatedEventArgs (
    ByVal row As DataRow,
    ByVal command As IDbCommand,
    ByVal statementType As StatementType,
    ByVal tableMapping As DataTableMapping
)
```

C\#
:   ```
public SARowUpdatedEventArgs (
    DataRow row,
    IDbCommand command,
    StatementType statementType,
    DataTableMapping tableMapping
)
```



## Parameters

row
:   The DataRow sent through an Update.

command
:   The IDbCommand executed when Update is called.

statementType
:   One of the StatementType values that specifies the type of query executed.

tableMapping
:   The DataTableMapping sent through an Update.

