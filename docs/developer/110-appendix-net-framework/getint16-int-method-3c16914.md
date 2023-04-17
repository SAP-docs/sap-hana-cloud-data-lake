<!-- loio3c1691476c5f1014ab8184d2ad789de3 -->

# GetInt16\(int\) Method

Returns the value of the specified column as a 16-bit signed integer.



Visual Basic
:   ```
Public Overrides Function GetInt16 (ByVal ordinal As Integer) As Short
```

C\#
:   ```
public override short GetInt16 (int ordinal)
```



## Parameters

ordinal
:   An ordinal number indicating the column from which the value is obtained. The numbering is zero-based.



## Returns

The value of the specified column.



## Remarks

No conversions are performed, so the data that is being retrieved must already be a 16-bit signed integer.

