<!-- loio3c1620576c5f101485afd8cf618fddf5 -->

# GetByte\(int\) Method

Returns the value of the specified column as a Byte.



Visual Basic
:   ```
Public Overrides Function GetByte (ByVal ordinal As Integer) As Byte
```

C\#
:   ```
public override byte GetByte (int ordinal)
```



## Parameters

ordinal
:   An ordinal number indicating the column from which the value is obtained. The numbering is zero-based.



## Returns

The value of the column.



## Remarks

No conversions are performed, so the data that is being retrieved must already be a byte.

