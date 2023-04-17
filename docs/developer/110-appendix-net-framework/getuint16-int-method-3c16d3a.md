<!-- loio3c16d3a46c5f1014a75ba57ef656b1f7 -->

# GetUInt16\(int\) Method

Returns the value of the specified column as a 16-bit unsigned integer.



Visual Basic
:   ```
Public Function GetUInt16 (ByVal ordinal As Integer) As UShort
```

C\#
:   ```
public ushort GetUInt16 (int ordinal)
```



## Parameters

ordinal
:   An ordinal number indicating the column from which the value is obtained. The numbering is zero-based.



## Returns

The value of the specified column.



## Remarks

No conversions are performed, so the data that is being retrieved must already be a 16-bit unsigned integer.

