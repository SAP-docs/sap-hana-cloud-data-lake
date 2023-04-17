<!-- loio3c15c40d6c5f1014b6f68fab5b7865f0 -->

# SelectCommand Property

Specifies an SACommand that is used during Fill or FillSchema to obtain a result set from the database for copying into a DataSet.



Visual Basic
:   ```
Public Shadows Property SelectCommand As SACommand
```

C\#
:   ```
public new SACommand SelectCommand {get;set;}
```



## Remarks

When SelectCommand is assigned to a previously created SACommand, the SACommand is not cloned. The SelectCommand maintains a reference to the previously created SACommand object.

If the SelectCommand does not return any rows, then no tables are added to the DataSet, and no exception is raised.

The SELECT statement can also be specified in the SADataAdapter constructor.

