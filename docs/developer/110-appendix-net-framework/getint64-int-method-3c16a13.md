<!-- loio3c16a1376c5f1014b2b7aa02849e1073 -->

# GetInt64\(int\) Method

Returns the value of the specified column as a 64-bit signed integer.



Visual Basic
:   ```
Public Overrides Function GetInt64 (ByVal ordinal As Integer) As Long
```

C\#
:   ```
public override long GetInt64 (int ordinal)
```



## Parameters

ordinal
:   An ordinal number indicating the column from which the value is obtained. The numbering is zero-based.



## Returns

The value of the specified column.



## Remarks

No conversions are performed, so the data that is being retrieved must already be a 64-bit signed integer.

