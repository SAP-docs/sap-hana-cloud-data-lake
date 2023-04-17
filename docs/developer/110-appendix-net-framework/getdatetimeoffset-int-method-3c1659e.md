<!-- loio3c1659ef6c5f10149cffb6796d8d8f74 -->

# GetDateTimeOffset\(int\) Method

Returns the value of the specified column as a DateTimeOffset object.



Visual Basic
:   ```
Public Function GetDateTimeOffset (ByVal ordinal As Integer) As DateTimeOffset
```

C\#
:   ```
public DateTimeOffset GetDateTimeOffset (int ordinal)
```



## Parameters

ordinal
:   The zero-based column ordinal.



## Returns

The value of the specified column.



## Remarks

No conversions are performed, so the data that is being retrieved must already be a DateTimeOffset object.

Call the SADataReader.IsDBNull method to check for null values before calling this method.

**Related Information**  


[IsDBNull\(int\) Method](isdbnull-int-method-3c171a9.md "Returns a value indicating whether the column contains NULL values.")

