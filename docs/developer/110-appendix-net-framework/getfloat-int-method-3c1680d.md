<!-- loio3c1680d76c5f10149176f4a4ac0937b2 -->

# GetFloat\(int\) Method

Returns the value of the specified column as a single-precision floating-point number.



Visual Basic
:   ```
Public Overrides Function GetFloat (ByVal ordinal As Integer) As Single
```

C\#
:   ```
public override float GetFloat (int ordinal)
```



## Parameters

ordinal
:   An ordinal number indicating the column from which the value is obtained. The numbering is zero-based.



## Returns

The value of the specified column.



## Remarks

No conversions are performed, so the data that is being retrieved must already be a single-precision floating-point number.

Call the SADataReader.IsDBNull method to check for null values before calling this method.

**Related Information**  


[IsDBNull\(int\) Method](isdbnull-int-method-3c171a9.md "Returns a value indicating whether the column contains NULL values.")

