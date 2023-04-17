<!-- loio3c1d81ef6c5f10148bf4bddb0f989caa -->

# SAParameterCollection Class

Represents all parameters to an SACommand object and, optionally, their mapping to a DataSet column.



Visual Basic
:   ```
Public NotInheritable Class SAParameterCollection Inherits System.Data.Common.DbParameterCollection
```

C\#
:   ```
public sealed class SAParameterCollection : System.Data.Common.DbParameterCollection
```



## Members

All members of SAParameterCollection, including inherited members.

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

public SAParameter



</td>
<td valign="top">

 [Add](add-method-3c1c351.md) 



</td>
<td valign="top">

Adds an SAParameter object to this collection.



</td>
</tr>
<tr>
<td valign="top">

public override void



</td>
<td valign="top">

 [AddRange](addrange-method-3c1c4c9.md) 



</td>
<td valign="top">

Adds an array of values to the end of the SAParameterCollection.



</td>
</tr>
<tr>
<td valign="top">

public SAParameter



</td>
<td valign="top">

 [AddWithValue\(string, object\)](addwithvalue-string-object-method-3c1c544.md) 



</td>
<td valign="top">

Adds a value to the end of this collection.



</td>
</tr>
<tr>
<td valign="top">

public override void



</td>
<td valign="top">

 [Clear\(\)](clear-method-3c1c5be.md) 



</td>
<td valign="top">

Removes all items from the collection.



</td>
</tr>
<tr>
<td valign="top">

public override bool



</td>
<td valign="top">

 [Contains](contains-method-3c1c72e.md) 



</td>
<td valign="top">

Indicates whether an SAParameter object exists in the collection.



</td>
</tr>
<tr>
<td valign="top">

public override void



</td>
<td valign="top">

 [CopyTo\(Array, int\)](copyto-array-int-method-3c1c7a8.md) 



</td>
<td valign="top">

Copies SAParameter objects from the SAParameterCollection to the specified array.



</td>
</tr>
<tr>
<td valign="top">

public override IEnumerator



</td>
<td valign="top">

 [GetEnumerator\(\)](getenumerator-method-3c1c9bc.md) 



</td>
<td valign="top">

Returns an enumerator that iterates through the SAParameterCollection.



</td>
</tr>
<tr>
<td valign="top">

protected override DbParameter



</td>
<td valign="top">

 [GetParameter](getparameter-method-3c1cca0.md) 



</td>
<td valign="top">

Returns a parameter from the SAParameterCollection object.



</td>
</tr>
<tr>
<td valign="top">

public override int



</td>
<td valign="top">

 [IndexOf](indexof-method-3c1cf09.md) 



</td>
<td valign="top">

Returns the location of the SAParameter object in the collection.



</td>
</tr>
<tr>
<td valign="top">

public override void



</td>
<td valign="top">

 [Insert\(int, object\)](insert-int-object-method-3c1cf87.md) 



</td>
<td valign="top">

Inserts an SAParameter object in the collection at the specified index.



</td>
</tr>
<tr>
<td valign="top">

public override void



</td>
<td valign="top">

 [Remove\(object\)](remove-object-method-3c1d225.md) 



</td>
<td valign="top">

Removes the specified SAParameter object from the collection.



</td>
</tr>
<tr>
<td valign="top">

public override void



</td>
<td valign="top">

 [RemoveAt](removeat-method-3c1d394.md) 



</td>
<td valign="top">

Removes the specified SAParameter object from the collection.



</td>
</tr>
<tr>
<td valign="top">

protected override void



</td>
<td valign="top">

 [SetParameter](setparameter-method-3c1d590.md) 



</td>
<td valign="top">

Sets a parameter in the SAParameterCollection object.



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

public override int



</td>
<td valign="top">

 [Count](count-property-3c1c820.md) 



</td>
<td valign="top">

Returns the number of SAParameter objects in the collection.



</td>
</tr>
<tr>
<td valign="top">

public override bool



</td>
<td valign="top">

 [IsFixedSize](isfixedsize-property-3c1d003.md) 



</td>
<td valign="top">

Gets a value that indicates whether the SAParameterCollection has a fixed size.



</td>
</tr>
<tr>
<td valign="top">

public override bool



</td>
<td valign="top">

 [IsReadOnly](isreadonly-property-3c1d0a8.md) 



</td>
<td valign="top">

Gets a value that indicates whether the SAParameterCollection is read-only.



</td>
</tr>
<tr>
<td valign="top">

public override bool



</td>
<td valign="top">

 [IsSynchronized](issynchronized-property-3c1d12e.md) 



</td>
<td valign="top">

Gets a value that indicates whether the SAParameterCollection object is synchronized.



</td>
</tr>
<tr>
<td valign="top">

public override object



</td>
<td valign="top">

 [SyncRoot](syncroot-property-3c1d618.md) 



</td>
<td valign="top">

Gets an object that can be used to synchronize access to the SAParameterCollection.



</td>
</tr>
<tr>
<td valign="top">

public new SAParameter



</td>
<td valign="top">

 [this](this-property-3c1d79e.md) 



</td>
<td valign="top">

Gets and sets the SAParameter object at the specified index.



</td>
</tr>
</table>



## Remarks

There is no constructor for SAParameterCollection. You obtain an SAParameterCollection object from the SACommand.Parameters property of an SACommand object.

**Related Information**  


[SACommand Class](sacommand-class-3c0ff5b.md "A SQL statement or stored procedure that is executed against a database.")

[Parameters Property](parameters-property-3c0f8d4.md "Specifies a collection of parameters for the current statement.")

[SAParameter Class](saparameter-class-3c1c008.md "Represents a parameter to an SACommand, and optionally, its mapping to a DataSet column.")

