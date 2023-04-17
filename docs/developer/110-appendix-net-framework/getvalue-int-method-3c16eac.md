<!-- loio3c16eacf6c5f1014bdfe9b53f6585e18 -->

# GetValue\(int\) Method

Returns the value of the specified column as an Object.



Visual Basic
:   ```
Public Overrides Function GetValue (ByVal ordinal As Integer) As Object
```

C\#
:   ```
public override object GetValue (int ordinal)
```



## Parameters

ordinal
:   An ordinal number indicating the column from which the value is obtained. The numbering is zero-based.



## Returns

The value of the specified column as an object.



## Remarks

This method returns DBNull for NULL database columns.

