<!-- loio3c1651ff6c5f1014badfff3e6a1dc486 -->

# GetDateTime\(int\) Method

Returns the value of the specified column as a DateTime object.



Visual Basic
:   ```
Public Overrides Function GetDateTime (ByVal ordinal As Integer) As Date
```

C\#
:   ```
public override DateTime GetDateTime (int ordinal)
```



## Parameters

ordinal
:   The zero-based column ordinal.



## Returns

The value of the specified column.



## Remarks

No conversions are performed, so the data that is being retrieved must already be a DateTime object.

Call the SADataReader.IsDBNull method to check for null values before calling this method.

**Related Information**  


[IsDBNull\(int\) Method](isdbnull-int-method-3c171a9.md "Returns a value indicating whether the column contains NULL values.")

