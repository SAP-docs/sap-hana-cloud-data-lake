<!-- loio3c1638846c5f10148e82f5fbdb543530 -->

# GetChars\(int, long, char\[\], int, int\) Method

Reads a stream of characters from the specified column offset into the buffer as an array starting at the given buffer offset.



Visual Basic
:   ```
Public Overrides Function GetChars (
    ByVal ordinal As Integer,
    ByVal dataIndex As Long,
    ByVal buffer As Char(),
    ByVal bufferIndex As Integer,
    ByVal length As Integer
) As Long
```

C\#
:   ```
public override unsafe long GetChars (
    int ordinal,
    long dataIndex,
    char[] buffer,
    int bufferIndex,
    int length
)
```



## Parameters

ordinal
:   The zero-based column ordinal.

dataIndex
:   The index within the row from which to begin the read operation.

buffer
:   The buffer into which to copy data.

bufferIndex
:   The index for buffer to begin the read operation.

length
:   The number of characters to read.



## Returns

The actual number of characters read.



## Remarks

GetChars returns the number of available characters in the field. In most cases this is the exact length of the field. However, the number returned may be less than the true length of the field if GetChars has already been used to obtain characters from the field. This may be the case, for example, when the SADataReader is reading a large data structure into a buffer.

If you pass a buffer that is a null reference \(Nothing in Visual Basic\), then GetChars returns the length of the field in characters.

No conversions are performed, so the data that is being retrieved must already be a character array.

For information about handling BLOBs, see "Data access and manipulation".

