<!-- loio3c16e2ec6c5f10149636d8de88aa39f5 -->

# GetUInt64\(int\) Method

Returns the value of the specified column as a 64-bit unsigned integer.



Visual Basic
:   ```
Public Function GetUInt64 (ByVal ordinal As Integer) As ULong
```

C\#
:   ```
public ulong GetUInt64 (int ordinal)
```



## Parameters

ordinal
:   An ordinal number indicating the column from which the value is obtained. The numbering is zero-based.



## Returns

The value of the specified column.



## Remarks

No conversions are performed, so the data that is being retrieved must already be a 64-bit unsigned integer.

