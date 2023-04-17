<!-- loio3c14eed86c5f10148d43ba9d3a5a935d -->

# DeleteCommand Property

Specifies an SACommand object that is executed against the database when the Update method is called to delete rows in the database that correspond to deleted rows in the DataSet.



Visual Basic
:   ```
Public Shadows Property DeleteCommand As SACommand
```

C\#
:   ```
public new SACommand DeleteCommand {get;set;}
```



## Remarks

If this property is not set and primary key information is present in the DataSet during Update, then DeleteCommand can be generated automatically by setting SelectCommand and using the SACommandBuilder. In that case, the SACommandBuilder generates any additional commands that you do not set. This generation logic requires key column information to be present in the SelectCommand.

When DeleteCommand is assigned to an existing SACommand object, the SACommand object is not cloned. The DeleteCommand maintains a reference to the existing SACommand.

**Related Information**  


[SelectCommand Property](selectcommand-property-3c15c40.md "Specifies an SACommand that is used during Fill or FillSchema to obtain a result set from the database for copying into a DataSet.")

