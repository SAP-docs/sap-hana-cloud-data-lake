<!-- loio3c1699296c5f1014a2b6eb41a3961ecd -->

# GetInt32\(int\) Method

Returns the value of the specified column as a 32-bit signed integer.



Visual Basic
:   ```
Public Overrides Function GetInt32 (ByVal ordinal As Integer) As Integer
```

C\#
:   ```
public override int GetInt32 (int ordinal)
```



## Parameters

ordinal
:   An ordinal number indicating the column from which the value is obtained. The numbering is zero-based.



## Returns

The value of the specified column.



## Remarks

No conversions are performed, so the data that is being retrieved must already be a 32-bit signed integer.

