<!-- loio3c16cbd06c5f101483fca592d3e50af2 -->

# GetTimeSpan\(int\) Method

Returns the value of the specified column as a TimeSpan object.



Visual Basic
:   ```
Public Function GetTimeSpan (ByVal ordinal As Integer) As TimeSpan
```

C\#
:   ```
public TimeSpan GetTimeSpan (int ordinal)
```



## Parameters

ordinal
:   An ordinal number indicating the column from which the value is obtained. The numbering is zero-based.



## Returns

The value of the specified column.



## Remarks

The column must be a TIME data type. The data is converted to TimeSpan. The Days property of TimeSpan is always set to 0.

Call SADataReader.IsDBNull method to check for NULL values before calling this method.

For more information, see "Data access and manipulation".

**Related Information**  


[IsDBNull\(int\) Method](isdbnull-int-method-3c171a9.md "Returns a value indicating whether the column contains NULL values.")

