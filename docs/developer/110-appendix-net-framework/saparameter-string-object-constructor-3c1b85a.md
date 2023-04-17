<!-- loio3c1b85a46c5f101481d8909be857f6fa -->

# SAParameter\(string, object\) Constructor

Initializes an SAParameter object with the specified parameter name and value.



Visual Basic
:   ```
Public Sub SAParameter (
    ByVal parameterName As String,
    ByVal value As Object
)
```

C\#
:   ```
public SAParameter (
    string parameterName,
    object value
)
```



## Parameters

parameterName
:   The name of the parameter.

value
:   An Object that is the value of the parameter.



## Remarks

This constructor is not recommended; it is provided for compatibility with other data providers.



The parameter name is "param" in the following example.

```
SELECT * FROM Customers WHERE ID = :param
```

