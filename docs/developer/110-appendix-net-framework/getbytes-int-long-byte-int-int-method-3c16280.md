<!-- loio3c16280f6c5f10149682c79e01ae9a89 -->

# GetBytes\(int, long, byte\[\], int, int\) Method

Reads a stream of bytes from the specified column offset into the buffer as an array, starting at the given buffer offset.



Visual Basic
:   ```
Public Overrides Function GetBytes (
    ByVal ordinal As Integer,
    ByVal dataIndex As Long,
    ByVal buffer As Byte(),
    ByVal bufferIndex As Integer,
    ByVal length As Integer
) As Long
```

C\#
:   ```
public override unsafe long GetBytes (
    int ordinal,
    long dataIndex,
    byte[] buffer,
    int bufferIndex,
    int length
)
```



## Parameters

ordinal
:   An ordinal number indicating the column from which the value is obtained. The numbering is zero-based.

dataIndex
:   The index within the column value from which to read bytes.

buffer
:   An array in which to store the data.

bufferIndex
:   The index in the array to start copying data.

length
:   The maximum length to copy into the specified buffer.



## Returns

The number of bytes read.



## Remarks

GetBytes returns the number of available bytes in the field. In most cases this is the exact length of the field. However, the number returned may be less than the true length of the field if GetBytes has already been used to obtain bytes from the field. This may be the case, for example, when the SADataReader is reading a large data structure into a buffer.

If you pass a buffer that is a null reference \(Nothing in Visual Basic\), then GetBytes returns the length of the field in bytes.

No conversions are performed, so the data that is being retrieved must already be a byte array.

