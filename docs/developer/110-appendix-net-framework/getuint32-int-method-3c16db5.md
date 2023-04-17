<!-- loio3c16db566c5f1014951bd8e657e5d70d -->

# GetUInt32\(int\) Method

Returns the value of the specified column as a 32-bit unsigned integer.



Visual Basic
:   ```
Public Function GetUInt32 (ByVal ordinal As Integer) As UInteger
```

C\#
:   ```
public uint GetUInt32 (int ordinal)
```



## Parameters

ordinal
:   An ordinal number indicating the column from which the value is obtained. The numbering is zero-based.



## Returns

The value of the specified column.



## Remarks

No conversions are performed, so the data that is being retrieved must already be a 32-bit unsigned integer.

