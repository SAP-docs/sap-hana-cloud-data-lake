<!-- loio3c1063c86c5f1014a804e1557767bd39 -->

# GetParameterPlaceholder\(int\) Method

Returns the placeholder for the parameter in the associated SQL statement.



Visual Basic
:   ```
Protected Overrides Function GetParameterPlaceholder (ByVal index As Integer) As String
```

C\#
:   ```
protected override string GetParameterPlaceholder (int index)
```



## Parameters

index
:   The number to be included as part of the parameter's name.



## Returns

The name of the parameter with the specified number appended.

