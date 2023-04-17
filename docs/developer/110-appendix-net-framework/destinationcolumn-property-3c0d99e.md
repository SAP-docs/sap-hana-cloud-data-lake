<!-- loio3c0d99ec6c5f1014908dea8095ed226e -->

# DestinationColumn Property

Gets or sets the name of the column in the destination database table being mapped to.



Visual Basic
:   ```
Public Property DestinationColumn As String
```

C\#
:   ```
public string DestinationColumn {get;set;}
```



## Remarks

A string specifying the name of the column in the destination table or a null reference \(Nothing in Visual Basic\) if the DestinationOrdinal property has priority.

The DestinationColumn property and DestinationOrdinal property are mutually exclusive. The most recently set value takes priority.

Setting the DestinationColumn property causes the DestinationOrdinal property to be set to -1. Setting the DestinationOrdinal property causes the DestinationColumn property to be set to a null reference \(Nothing in Visual Basic\).

It is an error to set DestinationColumn to null or the empty string.

**Related Information**  


[DestinationOrdinal Property](destinationordinal-property-3c0da4e.md "Gets or sets the ordinal value of the column in the destination table being mapped to.")

