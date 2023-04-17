<!-- loio3c1bc32e6c5f10149a96cd229e015cfc -->

# Size Property

Gets and sets the maximum size, in bytes, of the data within the column.



Visual Basic
:   ```
Public Overrides Property Size As Integer
```

C\#
:   ```
public override int Size {get;set;}
```



## Remarks

The value of this property is the maximum size, in bytes, of the data within the column. The default value is inferred from the parameter value.

The Size property is used for binary and string types.

For variable length data types, the Size property describes the maximum amount of data to transmit to the database server. For example, the Size property can be used to limit the amount of data sent to the database server for a string value to the first one hundred bytes.

If Size is not explicitly set, then it is inferred from the actual size of the specified parameter value. For fixed width data types, the value of Size is ignored. It can be retrieved for informational purposes, and returns the maximum amount of bytes the provider uses when transmitting the value of the parameter to the database server.

