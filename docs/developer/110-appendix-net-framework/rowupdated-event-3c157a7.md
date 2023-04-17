<!-- loio3c157a7d6c5f101495b180a070091157 -->

# RowUpdated Event

Occurs during an update after a command is executed against the data source.



Visual Basic
:   ```
Public Event RowUpdated  As SARowUpdatedEventHandler
```

C\#
:   ```
public SARowUpdatedEventHandler RowUpdated;
```



## Remarks

When an attempt to update is made, the event fires.

The event handler receives an argument of type SARowUpdatedEventArgs containing data related to this event.

For more information, see the .NET Framework documentation for OleDbDataAdapter.RowUpdated Event.

