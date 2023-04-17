<!-- loio3c1618926c5f1014b2ca8cf3b375b498 -->

# GetBoolean\(int\) Method

Returns the value of the specified column as a Boolean.



Visual Basic
:   ```
Public Overrides Function GetBoolean (ByVal ordinal As Integer) As Boolean
```

C\#
:   ```
public override bool GetBoolean (int ordinal)
```



## Parameters

ordinal
:   An ordinal number indicating the column from which the value is obtained. The numbering is zero-based.



## Returns

The value of the column.



## Remarks

No conversions are performed, so the data that is being retrieved must already be a Boolean.

**Related Information**  


[GetOrdinal\(string\) Method](getordinal-string-method-3c16b3a.md "Returns the column ordinal, given the column name.")

[GetFieldType\(int\) Method](getfieldtype-int-method-3c16794.md "Returns the Type that is the data type of the object.")

