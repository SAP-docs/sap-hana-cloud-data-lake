<!-- loio3c16c2f16c5f1014957681a8824ce342 -->

# GetString\(int\) Method

Returns the value of the specified column as a string.



Visual Basic
:   ```
Public Overrides Function GetString (ByVal ordinal As Integer) As String
```

C\#
:   ```
public override string GetString (int ordinal)
```



## Parameters

ordinal
:   An ordinal number indicating the column from which the value is obtained. The numbering is zero-based.



## Returns

The value of the specified column.



## Remarks

No conversions are performed, so the data that is being retrieved must already be a string.

Call the SADataReader.IsDBNull method to check for NULL values before calling this method.

**Related Information**  


[IsDBNull\(int\) Method](isdbnull-int-method-3c171a9.md "Returns a value indicating whether the column contains NULL values.")

