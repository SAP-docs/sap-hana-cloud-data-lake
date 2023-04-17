<!-- loio3c0fbf5b6c5f1014a6d2bdc0474a8747 -->

# SACommand\(string, SAConnection\) Constructor

A SQL statement or stored procedure that is executed against a database.



Visual Basic
:   ```
Public Sub SACommand (
    ByVal cmdText As String,
    ByVal connection As SAConnection
)
```

C\#
:   ```
public SACommand (
    string cmdText,
    SAConnection connection
)
```



## Parameters

cmdText
:   The text of the SQL statement or stored procedure. For parameterized statements, use a question mark \(?\) placeholder to pass parameters.

connection
:   The current connection.

