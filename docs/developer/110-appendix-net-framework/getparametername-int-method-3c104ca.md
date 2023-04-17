<!-- loio3c104cad6c5f10148227f63715c06059 -->

# GetParameterName\(int\) Method

Returns the name of the specified parameter in the format of @p\#.



Visual Basic
:   ```
Protected Overrides Function GetParameterName (ByVal index As Integer) As String
```

C\#
:   ```
protected override string GetParameterName (int index)
```



## Parameters

index
:   The number to be included as part of the parameter's name.



## Returns

The name of the parameter with the specified number appended as part of the parameter name.



## Remarks

Use when building a custom command builder.

