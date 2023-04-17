<!-- loio3c1254e36c5f10149947d6191b8bf3a2 -->

# StateChange Event

Occurs when the state of the SAConnection object changes.



Visual Basic
:   ```
Public Event StateChange  As StateChangeEventHandler
```

C\#
:   ```
public override StateChangeEventHandler StateChange;
```



## Remarks

The event handler receives an argument of type StateChangeEventArgs with data related to this event. The following StateChangeEventArgs properties provide information specific to this event: CurrentState and OriginalState.

For more information, see the .NET Framework documentation for OleDbConnection.StateChange Event.

