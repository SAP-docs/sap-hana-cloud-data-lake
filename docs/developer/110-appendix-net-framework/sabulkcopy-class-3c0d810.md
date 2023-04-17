<!-- loio3c0d81046c5f101495ef8d997706b40f -->

# SABulkCopy Class

Efficiently bulk load a database table with data from another source.



Visual Basic
:   ```
Public NotInheritable Class SABulkCopy Implements System.IDisposable
```

C\#
:   ```
public sealed class SABulkCopy : System.IDisposable
```



## Members

All members of SABulkCopy, including inherited members.

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

 [SABulkCopy](sabulkcopy-constructor-3c0d35a.md) 



</td>
<td valign="top">

Initializes an SABulkCopy object.



</td>
</tr>
</table>

 **Methods** 


<table>
<tr>
<th valign="top">

Modifier and Type



</th>
<th valign="top">

Method



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

public void



</td>
<td valign="top">

 [Close\(\)](close-method-3c0ce34.md) 



</td>
<td valign="top">

Closes the SABulkCopy instance.



</td>
</tr>
<tr>
<td valign="top">

public void



</td>
<td valign="top">

 [Dispose\(\)](dispose-method-3c0d03c.md) 



</td>
<td valign="top">

Disposes of the SABulkCopy instance.



</td>
</tr>
<tr>
<td valign="top">

public void



</td>
<td valign="top">

 [WriteToServer](writetoserver-method-3c0d749.md) 



</td>
<td valign="top">

Copies all rows in the supplied array of System.Data.DataRow objects to a destination table specified by the DestinationTableName property of the SABulkCopy object.



</td>
</tr>
<tr>
<td valign="top">

public Task



</td>
<td valign="top">

 [WriteToServerAsync](writetoserverasync-method-81de23c.md) 



</td>
<td valign="top">

Copies all rows from the supplied System.Data.DataRow array to a destination table specified by the SABulkCopy.DestinationTableName property of the SABulkCopy object.



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

public int



</td>
<td valign="top">

 [BatchSize](batchsize-property-3c0cd3f.md) 



</td>
<td valign="top">

Gets or sets the number of rows in each batch.



</td>
</tr>
<tr>
<td valign="top">

public int



</td>
<td valign="top">

 [BulkCopyTimeout](bulkcopytimeout-property-3c0cdbd.md) 



</td>
<td valign="top">

Gets or sets the number of seconds for the operation to complete before it times out.



</td>
</tr>
<tr>
<td valign="top">

public SABulkCopyColumnMappingCollection



</td>
<td valign="top">

 [ColumnMappings](columnmappings-property-3c0ceb4.md) 



</td>
<td valign="top">

Returns a collection of SABulkCopyColumnMapping items.



</td>
</tr>
<tr>
<td valign="top">

public string



</td>
<td valign="top">

 [DestinationTableName](destinationtablename-property-3c0cf31.md) 



</td>
<td valign="top">

Gets or sets the name of the destination table on the database server.



</td>
</tr>
<tr>
<td valign="top">

public int



</td>
<td valign="top">

 [NotifyAfter](notifyafter-property-3c0d0b7.md) 



</td>
<td valign="top">

Gets or sets the number of rows to be processed before generating a notification event.



</td>
</tr>
</table>

 **Events** 


<table>
<tr>
<th valign="top">

Modifier and Type



</th>
<th valign="top">

Event



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

public SARowsCopiedEventHandler



</td>
<td valign="top">

 [SARowsCopied](sarowscopied-event-3c0d3db.md) 



</td>
<td valign="top">

This event occurs every time the number of rows specified by the NotifyAfter property have been processed.



</td>
</tr>
</table>



## Remarks

 *Implements:* System.IDisposable

