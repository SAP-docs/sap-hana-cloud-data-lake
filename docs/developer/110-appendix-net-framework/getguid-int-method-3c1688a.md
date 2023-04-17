<!-- loio3c1688a06c5f1014a28a9eb3869f42f2 -->

# GetGuid\(int\) Method

Returns the value of the specified column as a global unique identifier \(GUID\).



Visual Basic
:   ```
Public Overrides Function GetGuid (ByVal ordinal As Integer) As Guid
```

C\#
:   ```
public override Guid GetGuid (int ordinal)
```



## Parameters

ordinal
:   An ordinal number indicating the column from which the value is obtained. The numbering is zero-based.



## Returns

The value of the specified column.



## Remarks

The data that is being retrieved must already be a globally-unique identifier or binary\(16\).

Call the SADataReader.IsDBNull method to check for null values before calling this method.

**Related Information**  


[IsDBNull\(int\) Method](isdbnull-int-method-3c171a9.md "Returns a value indicating whether the column contains NULL values.")

