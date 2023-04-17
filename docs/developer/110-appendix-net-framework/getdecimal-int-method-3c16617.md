<!-- loio3c1661766c5f1014ae3494d16904af6b -->

# GetDecimal\(int\) Method

Returns the value of the specified column as a Decimal object.



Visual Basic
:   ```
Public Overrides Function GetDecimal (ByVal ordinal As Integer) As Decimal
```

C\#
:   ```
public override decimal GetDecimal (int ordinal)
```



## Parameters

ordinal
:   An ordinal number indicating the column from which the value is obtained. The numbering is zero-based.



## Returns

The value of the specified column.



## Remarks

No conversions are performed, so the data that is being retrieved must already be a Decimal object.

Call the SADataReader.IsDBNull method to check for null values before calling this method.

**Related Information**  


[IsDBNull\(int\) Method](isdbnull-int-method-3c171a9.md "Returns a value indicating whether the column contains NULL values.")

