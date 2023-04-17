<!-- loio3c1630c06c5f1014a6f6d5d42c6fb3ae -->

# GetChar\(int\) Method

Returns the value of the specified column as a character.



Visual Basic
:   ```
Public Overrides Function GetChar (ByVal ordinal As Integer) As Char
```

C\#
:   ```
public override char GetChar (int ordinal)
```



## Parameters

ordinal
:   An ordinal number indicating the column from which the value is obtained. The numbering is zero-based.



## Returns

The value of the column.



## Remarks

No conversions are performed, so the data that is being retrieved must already be a character.

Call the SADataReader.IsDBNull method to check for null values before calling this method.

**Related Information**  


[IsDBNull\(int\) Method](isdbnull-int-method-3c171a9.md "Returns a value indicating whether the column contains NULL values.")

