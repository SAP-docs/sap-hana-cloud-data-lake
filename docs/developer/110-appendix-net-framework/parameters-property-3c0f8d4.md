<!-- loio3c0f8d416c5f101496b2d915cc8c1113 -->

# Parameters Property

Specifies a collection of parameters for the current statement.



Visual Basic
:   ```
Public ReadOnly Shadows Property Parameters As SAParameterCollection
```

C\#
:   ```
public new SAParameterCollection Parameters {get;}
```



## Remarks

Use question marks in the CommandText to indicate parameters.

The parameters of the SQL statement or stored procedure. The default value is an empty collection.

When CommandType is set to Text, pass parameters using the question mark placeholder. For example:

```
SELECT * FROM Customers WHERE ID = ?
```

The order in which SAParameter objects are added to the SAParameterCollection must directly correspond to the position of the question mark placeholder for the parameter in the command text.

When the parameters in the collection do not match the requirements of the query to be executed, an error may result or an exception may be thrown.

**Related Information**  


[SAParameterCollection Class](saparametercollection-class-3c1d81e.md "Represents all parameters to an SACommand object and, optionally, their mapping to a DataSet column.")

