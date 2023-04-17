<!-- loio3c0df4c96c5f1014ad45ba2895a10d22 -->

# SourceColumn Property

Gets or sets the name of the column being mapped in the data source.



Visual Basic
:   ```
Public Property SourceColumn As String
```

C\#
:   ```
public string SourceColumn {get;set;}
```



## Remarks

A string specifying the name of the column in the data source or a null reference \(Nothing in Visual Basic\) if the SourceOrdinal property has priority.

The SourceColumn property and SourceOrdinal property are mutually exclusive. The most recently set value takes priority.

Setting the SourceColumn property causes the SourceOrdinal property to be set to -1. Setting the SourceOrdinal property causes the SourceColumn property to be set to a null reference \(Nothing in Visual Basic\).

It is an error to set SourceColumn to null or the empty string.

**Related Information**  


[SourceOrdinal Property](sourceordinal-property-3c0dfc8.md "Gets or sets ordinal position of the source column within the data source.")

