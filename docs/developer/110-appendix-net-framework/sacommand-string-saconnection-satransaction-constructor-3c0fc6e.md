<!-- loio3c0fc6ea6c5f1014878796d284ad0f31 -->

# SACommand\(string, SAConnection, SATransaction\) Constructor

A SQL statement or stored procedure that is executed against a database.



Visual Basic
:   ```
Public Sub SACommand (
    ByVal cmdText As String,
    ByVal connection As SAConnection,
    ByVal transaction As SATransaction
)
```

C\#
:   ```
public SACommand (
    string cmdText,
    SAConnection connection,
    SATransaction transaction
)
```



## Parameters

cmdText
:   The text of the SQL statement or stored procedure. For parameterized statements, use a question mark \(?\) placeholder to pass parameters.

connection
:   The current connection.

transaction
:   The SATransaction object in which the SAConnection executes.

**Related Information**  


[SATransaction Class](satransaction-class-3c1f791.md "Represents a SQL transaction.")

