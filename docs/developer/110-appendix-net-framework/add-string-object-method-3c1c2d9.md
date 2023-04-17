<!-- loio3c1c2d9c6c5f10149e6fc133e9d97e23 -->

# Add\(string, object\) Method

Adds an SAParameter object to this collection, created using the specified parameter name and value, to the collection.



Visual Basic
:   ```
Public Function Add (
    ByVal parameterName As String,
    ByVal value As Object
) As SAParameter
```

C\#
:   ```
public SAParameter Add (
    string parameterName,
    object value
)
```



## Parameters

parameterName
:   The name of the parameter.

value
:   The value of the parameter to add to the connection.



## Returns

The new SAParameter object.



## Remarks

Because of the special treatment of the 0 and 0.0 constants and the way overloaded methods are resolved, explicitly cast constant values to the desired object type when using this method.

**Related Information**  


[SAParameter Class](saparameter-class-3c1c008.md "Represents a parameter to an SACommand, and optionally, its mapping to a DataSet column.")

