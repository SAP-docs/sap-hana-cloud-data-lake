<!-- loio3c171a966c5f1014873d8fc6efe8e306 -->

# IsDBNull\(int\) Method

Returns a value indicating whether the column contains NULL values.



Visual Basic
:   ```
Public Overrides Function IsDBNull (ByVal ordinal As Integer) As Boolean
```

C\#
:   ```
public override bool IsDBNull (int ordinal)
```



## Parameters

ordinal
:   The zero-based column ordinal.



## Returns

True if the specified column value is equivalent to DBNull; false otherwise.



## Remarks

Call this method to check for NULL column values before calling the typed get methods \(for example, GetByte, GetChar, and so on\) to avoid raising an exception.

