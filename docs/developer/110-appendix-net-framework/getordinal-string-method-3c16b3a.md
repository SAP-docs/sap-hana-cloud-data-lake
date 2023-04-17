<!-- loio3c16b3a36c5f101495b0b6d8b86e620d -->

# GetOrdinal\(string\) Method

Returns the column ordinal, given the column name.



Visual Basic
:   ```
Public Overrides Function GetOrdinal (ByVal name As String) As Integer
```

C\#
:   ```
public override int GetOrdinal (string name)
```



## Parameters

name
:   The column name.



## Returns

The zero-based column ordinal.



## Remarks

GetOrdinal performs a case-sensitive lookup first. If it fails, then a second case-insensitive search is made.

GetOrdinal is Japanese kana-width insensitive.

Because ordinal-based lookups are more efficient than named lookups, it is inefficient to call GetOrdinal within a loop. Save time by calling GetOrdinal once and assigning the results to an integer variable for use within the loop.

