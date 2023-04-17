<!-- loio3c0e056a6c5f1014aeccdd51288d6acd -->

# SABulkCopyColumnMapping Class

Defines the mapping between a column in an SABulkCopy instance's data source and a column in the instance's destination table.



Visual Basic
:   ```
Public NotInheritable Class SABulkCopyColumnMapping
```

C\#
:   ```
public sealed class SABulkCopyColumnMapping
```



## Members

All members of SABulkCopyColumnMapping, including inherited members.

 **Constructors** 


<table>
<tr>
<th valign="top">

Modifier and Type



</th>
<th valign="top">

Constructor



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

public



</td>
<td valign="top">

 [SABulkCopyColumnMapping](sabulkcopycolumnmapping-constructor-3c0ddc5.md) 



</td>
<td valign="top">

Creates a new column mapping, using column ordinals or names to refer to source and destination columns.



</td>
</tr>
</table>

 **Properties** 


<table>
<tr>
<th valign="top">

Modifier and Type



</th>
<th valign="top">

Property



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

public string



</td>
<td valign="top">

 [DestinationColumn](destinationcolumn-property-3c0d99e.md) 



</td>
<td valign="top">

Gets or sets the name of the column in the destination database table being mapped to.



</td>
</tr>
<tr>
<td valign="top">

public int



</td>
<td valign="top">

 [DestinationOrdinal](destinationordinal-property-3c0da4e.md) 



</td>
<td valign="top">

Gets or sets the ordinal value of the column in the destination table being mapped to.



</td>
</tr>
<tr>
<td valign="top">

public string



</td>
<td valign="top">

 [SourceColumn](sourcecolumn-property-3c0df4c.md) 



</td>
<td valign="top">

Gets or sets the name of the column being mapped in the data source.



</td>
</tr>
<tr>
<td valign="top">

public int



</td>
<td valign="top">

 [SourceOrdinal](sourceordinal-property-3c0dfc8.md) 



</td>
<td valign="top">

Gets or sets ordinal position of the source column within the data source.



</td>
</tr>
</table>

