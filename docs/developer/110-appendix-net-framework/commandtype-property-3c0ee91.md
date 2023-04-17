<!-- loio3c0ee9126c5f1014b6dac5d9240a6a70 -->

# CommandType Property

Gets or sets the type of command represented by an SACommand.



Visual Basic
:   ```
Public Overrides Property CommandType As CommandType
```

C\#
:   ```
public override CommandType CommandType {get;set;}
```



## Remarks

One of the System.Data.CommandType values. The default is System.Data.CommandType.Text.

Supported command types are as follows:

-   System.Data.CommandType.StoredProcedure When you specify this CommandType, the command text must be the name of a stored procedure and you must supply any arguments as SAParameter objects.
-   System.Data.CommandType.Text This is the default value.

When the CommandType property is set to StoredProcedure, the CommandText property should be set to the name of the stored procedure. The command executes this stored procedure when you call one of the Execute methods.

Use a question mark \(?\) placeholder to pass parameters. For example:

```
SELECT * FROM Customers WHERE ID = ?
```

The order in which SAParameter objects are added to the SAParameterCollection must directly correspond to the position of the question mark placeholder for the parameter.

