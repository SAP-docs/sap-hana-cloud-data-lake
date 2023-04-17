<!-- loio3c0da4ee6c5f1014b00ceb0ec2989284 -->

# DestinationOrdinal Property

Gets or sets the ordinal value of the column in the destination table being mapped to.



Visual Basic
:   ```
Public Property DestinationOrdinal As Integer
```

C\#
:   ```
public int DestinationOrdinal {get;set;}
```



## Remarks

An integer specifying the ordinal of the column being mapped to in the destination table or -1 if the property is not set.

The DestinationColumn property and DestinationOrdinal property are mutually exclusive. The most recently set value takes priority.

Setting the DestinationColumn property causes the DestinationOrdinal property to be set to -1. Setting the DestinationOrdinal property causes the DestinationColumn property to be set to a null reference \(Nothing in Visual Basic\).

**Related Information**  


[DestinationColumn Property](destinationcolumn-property-3c0d99e.md "Gets or sets the name of the column in the destination database table being mapped to.")

