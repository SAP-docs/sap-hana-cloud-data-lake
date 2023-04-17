<!-- loio3c1b7d4c6c5f101492c9ee39d28f2029 -->

# SAParameter\(string, SADbType, int, string\) Constructor

Initializes an SAParameter object with the specified parameter name, data type, size, and source column.



Visual Basic
:   ```
Public Sub SAParameter (
    ByVal parameterName As String,
    ByVal dbType As SADbType,
    ByVal size As Integer,
    ByVal sourceColumn As String
)
```

C\#
:   ```
public SAParameter (
    string parameterName,
    SADbType dbType,
    int size,
    string sourceColumn
)
```



## Parameters

parameterName
:   The name of the parameter.

dbType
:   One of the SADbType values.

size
:   The length of the parameter.

sourceColumn
:   The name of the source column to map.



The parameter name is "param" in the following example.

```
SELECT * FROM Customers WHERE ID = :param
```

