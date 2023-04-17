<!-- loio3c16698d6c5f10148205e857cbf0392a -->

# GetDouble\(int\) Method

Returns the value of the specified column as a double-precision floating-point number.



Visual Basic
:   ```
Public Overrides Function GetDouble (ByVal ordinal As Integer) As Double
```

C\#
:   ```
public override double GetDouble (int ordinal)
```



## Parameters

ordinal
:   An ordinal number indicating the column from which the value is obtained. The numbering is zero-based.



## Returns

The value of the specified column.



## Remarks

No conversions are performed, so the data that is being retrieved must already be a double-precision floating-point number.

Call the SADataReader.IsDBNull method to check for null values before calling this method.

**Related Information**  


[IsDBNull\(int\) Method](isdbnull-int-method-3c171a9.md "Returns a value indicating whether the column contains NULL values.")

