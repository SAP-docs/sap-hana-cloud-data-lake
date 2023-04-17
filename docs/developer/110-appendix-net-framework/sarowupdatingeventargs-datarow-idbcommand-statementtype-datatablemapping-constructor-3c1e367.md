<!-- loio3c1e36776c5f1014a11bbc670c389e47 -->

# SARowUpdatingEventArgs\(DataRow, IDbCommand, StatementType, DataTableMapping\) Constructor

Initializes a new instance of the SARowUpdatingEventArgs class.



Visual Basic
:   ```
Public Sub SARowUpdatingEventArgs (
    ByVal row As DataRow,
    ByVal command As IDbCommand,
    ByVal statementType As StatementType,
    ByVal tableMapping As DataTableMapping
)
```

C\#
:   ```
public SARowUpdatingEventArgs (
    DataRow row,
    IDbCommand command,
    StatementType statementType,
    DataTableMapping tableMapping
)
```



## Parameters

row
:   The DataRow to update.

command
:   The IDbCommand to execute during update.

statementType
:   One of the StatementType values that specifies the type of query executed.

tableMapping
:   The DataTableMapping sent through an Update.

