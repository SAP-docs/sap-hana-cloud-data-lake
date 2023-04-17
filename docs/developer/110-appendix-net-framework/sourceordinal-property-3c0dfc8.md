<!-- loio3c0dfc876c5f1014b1eaf7548cdd86b0 -->

# SourceOrdinal Property

Gets or sets ordinal position of the source column within the data source.



Visual Basic
:   ```
Public Property SourceOrdinal As Integer
```

C\#
:   ```
public int SourceOrdinal {get;set;}
```



## Remarks

An integer specifying the ordinal of the column in the data source or -1 if the property is not set.

The SourceColumn property and SourceOrdinal property are mutually exclusive. The most recently set value takes priority.

Setting the SourceColumn property causes the SourceOrdinal property to be set to -1. Setting the SourceOrdinal property causes the SourceColumn property to be set to a null reference \(Nothing in Visual Basic\).

**Related Information**  


[SourceColumn Property](sourcecolumn-property-3c0df4c.md "Gets or sets the name of the column being mapped in the data source.")

