<!-- loio3c1bf1a46c5f101495a685fec0e131c0 -->

# Value Property

Gets and sets the value of the parameter.



Visual Basic
:   ```
Public Overrides Property Value As Object
```

C\#
:   ```
public override object Value {get;set;}
```



## Remarks

An Object that specifies the value of the parameter.

For input parameters, the value is bound to the SACommand that is sent to the database server. For output and return value parameters, the value is set on completion of the SACommand and after the SADataReader is closed.

When sending a null parameter value to the database server, specify DBNull, not null. The null value in the system is an empty object that has no value. DBNull is used to represent null values.

If the application specifies the database type, then the bound value is converted to that type when the .NET Data Provider sends the data to the database server. The provider attempts to convert any type of value if it supports the IConvertible interface. Conversion errors may result if the specified type is not compatible with the value.

Both the DbType and SADbType properties can be inferred by setting the Value.

The Value property is overwritten by Update.

