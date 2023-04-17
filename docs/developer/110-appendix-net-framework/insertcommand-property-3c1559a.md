<!-- loio3c1559af6c5f10148237a79dd2af644a -->

# InsertCommand Property

Specifies an SACommand that is executed against the database when the Update method is called that adds rows to the database to correspond to rows that were inserted in the DataSet.



Visual Basic
:   ```
Public Shadows Property InsertCommand As SACommand
```

C\#
:   ```
public new SACommand InsertCommand {get;set;}
```



## Remarks

The SACommandBuilder does not require key columns to generate InsertCommand.

When InsertCommand is assigned to an existing SACommand object, the SACommand is not cloned. The InsertCommand maintains a reference to the existing SACommand.

If this command returns rows, then the rows may be added to the DataSet depending on how you set the UpdatedRowSource property of the SACommand object.

