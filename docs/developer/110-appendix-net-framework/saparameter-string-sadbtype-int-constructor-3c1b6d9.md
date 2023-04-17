<!-- loio3c1b6d926c5f1014a2afd1aa05d26f81 -->

# SAParameter\(string, SADbType, int\) Constructor

Initializes an SAParameter object with the specified parameter name, data type, and size.



Visual Basic
:   ```
Public Sub SAParameter (
    ByVal parameterName As String,
    ByVal dbType As SADbType,
    ByVal size As Integer
)
```

C\#
:   ```
public SAParameter (
    string parameterName,
    SADbType dbType,
    int size
)
```



## Parameters

parameterName
:   The name of the parameter.

dbType
:   One of the SADbType values.

size
:   The length of the parameter.



The parameter name is "param" in the following example.

```
SELECT * FROM Customers WHERE ID = :param
```

