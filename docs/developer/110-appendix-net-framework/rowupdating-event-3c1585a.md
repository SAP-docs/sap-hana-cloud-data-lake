<!-- loio3c1585a46c5f1014b6abce1ef28161fa -->

# RowUpdating Event

Occurs during an update before a command is executed against the data source.



Visual Basic
:   ```
Public Event RowUpdating  As SARowUpdatingEventHandler
```

C\#
:   ```
public SARowUpdatingEventHandler RowUpdating;
```



## Remarks

When an attempt to update is made, the event fires.

The event handler receives an argument of type SARowUpdatingEventArgs containing data related to this event.

For more information, see the .NET Framework documentation for OleDbDataAdapter.RowUpdating Event.

