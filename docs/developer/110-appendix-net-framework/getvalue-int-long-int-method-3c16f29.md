<!-- loio3c16f2926c5f1014a6cb8f30eb51d719 -->

# GetValue\(int, long, int\) Method

Returns a substring of the value of the specified column as an Object.



Visual Basic
:   ```
Public Function GetValue (
    ByVal ordinal As Integer,
    ByVal index As Long,
    ByVal length As Integer
) As Object
```

C\#
:   ```
public object GetValue (
    int ordinal,
    long index,
    int length
)
```



## Parameters

ordinal
:   An ordinal number indicating the column from which the value is obtained. The numbering is zero-based.

index
:   A zero-based index of the substring of the value to be obtained.

length
:   The length of the substring of the value to be obtained.



## Returns

The substring value is returned as an object.



## Remarks

This method returns DBNull for NULL database columns.

