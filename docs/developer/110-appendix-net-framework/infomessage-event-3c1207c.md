<!-- loio3c1207c06c5f10148b22e898d27a0c5c -->

# InfoMessage Event

Occurs when the database server returns a warning or informational message.



Visual Basic
:   ```
Public Event InfoMessage  As SAInfoMessageEventHandler
```

C\#
:   ```
public SAInfoMessageEventHandler InfoMessage;
```



## Remarks

The event handler receives an argument of type SAInfoMessageEventArgs containing data related to this event. The following SAInfoMessageEventArgs properties provide information specific to this event: NativeError, Errors, Message, MessageType, and Source.

For more information, see the .NET Framework documentation for OleDbConnection.InfoMessage Event.

