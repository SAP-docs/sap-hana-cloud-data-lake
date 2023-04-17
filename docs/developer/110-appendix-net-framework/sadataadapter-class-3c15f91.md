<!-- loio3c15f9136c5f10149255bd0038ff43ca -->

# SADataAdapter Class

Represents a set of commands and a database connection used to fill a System.Data.DataSet and to update a database.



Visual Basic
:   ```
Public NotInheritable Class SADataAdapter Inherits System.Data.Common.DbDataAdapter Implements System.ICloneable
```

C\#
:   ```
public sealed class SADataAdapter : System.Data.Common.DbDataAdapter, System.ICloneable
```



## Members

All members of SADataAdapter, including inherited members.

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

 [SADataAdapter](sadataadapter-constructor-3c15bab.md) 



</td>
<td valign="top">

Initializes an SADataAdapter object.



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

protected override void



</td>
<td valign="top">

 [ClearBatch\(\)](clearbatch-method-3c14cf6.md) 



</td>
<td valign="top">

Removes all SACommand objects from the batch.



</td>
</tr>
<tr>
<td valign="top">

protected override RowUpdatedEventArgs



</td>
<td valign="top">

 [CreateRowUpdatedEvent\(DataRow, IDbCommand, StatementType, DataTableMapping\)](createrowupdatedevent-datarow-idbcommand-statementtype-datatablemapping-method-3c14df4.md) 



</td>
<td valign="top">

Initializes a new instance of the System.Data.Common.RowUpdatedEventArgs class.



</td>
</tr>
<tr>
<td valign="top">

protected override RowUpdatingEventArgs



</td>
<td valign="top">

 [CreateRowUpdatingEvent\(DataRow, IDbCommand, StatementType, DataTableMapping\)](createrowupdatingevent-datarow-idbcommand-statementtype-datatablemapping-method-3c14e70.md) 



</td>
<td valign="top">

Initializes a new instance of the System.Data.Common.RowUpdatingEventArgs class.



</td>
</tr>
<tr>
<td valign="top">

protected override void



</td>
<td valign="top">

 [Dispose\(bool\)](dispose-bool-method-3c14f68.md) 



</td>
<td valign="top">

Releases the unmanaged resources used by the SADataAdapter object and optionally releases the managed resources.



</td>
</tr>
<tr>
<td valign="top">

protected override int



</td>
<td valign="top">

 [Fill](fill-method-3c150dd.md) 



</td>
<td valign="top">

Adds or refreshes rows in a System.Data.DataSet or System.Data.DataTable object with data from the database.



</td>
</tr>
<tr>
<td valign="top">

protected override DataTable\[\]



</td>
<td valign="top">

 [FillSchema](fillschema-method-3c1538a.md) 



</td>
<td valign="top">

Adds a System.Data.DataTable to a System.Data.DataSet and configures the schema to match the schema in the data source.



</td>
</tr>
<tr>
<td valign="top">

public new SAParameter\[\]



</td>
<td valign="top">

 [GetFillParameters\(\)](getfillparameters-method-3c15439.md) 



</td>
<td valign="top">

Returns the parameters set by you when executing a SELECT statement.



</td>
</tr>
<tr>
<td valign="top">

protected override void



</td>
<td valign="top">

 [InitializeBatching\(\)](initializebatching-method-3c154e9.md) 



</td>
<td valign="top">

Initializes batching for the SADataAdapter object.



</td>
</tr>
<tr>
<td valign="top">

protected override void



</td>
<td valign="top">

 [OnRowUpdated\(RowUpdatedEventArgs\)](onrowupdated-rowupdatedeventargs-method-3c15649.md) 



</td>
<td valign="top">

Raises the RowUpdated event of a .NET Framework data provider.



</td>
</tr>
<tr>
<td valign="top">

protected override void



</td>
<td valign="top">

 [OnRowUpdating\(RowUpdatingEventArgs\)](onrowupdating-rowupdatingeventargs-method-3c156f9.md) 



</td>
<td valign="top">

Raises the RowUpdating event of a .NET Framework data provider.



</td>
</tr>
<tr>
<td valign="top">

protected override void



</td>
<td valign="top">

 [TerminateBatching\(\)](terminatebatching-method-3c15d7e.md) 



</td>
<td valign="top">

Ends batching for the SADataAdapter object.



</td>
</tr>
<tr>
<td valign="top">

protected override int



</td>
<td valign="top">

 [Update\(DataRow\[\], DataTableMapping\)](update-datarow-datatablemapping-method-3c15e06.md) 



</td>
<td valign="top">

Updates the tables in a database with the changes made to the DataSet.



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

public new SACommand



</td>
<td valign="top">

 [DeleteCommand](deletecommand-property-3c14eed.md) 



</td>
<td valign="top">

Specifies an SACommand object that is executed against the database when the Update method is called to delete rows in the database that correspond to deleted rows in the DataSet.



</td>
</tr>
<tr>
<td valign="top">

public new SACommand



</td>
<td valign="top">

 [InsertCommand](insertcommand-property-3c1559a.md) 



</td>
<td valign="top">

Specifies an SACommand that is executed against the database when the Update method is called that adds rows to the database to correspond to rows that were inserted in the DataSet.



</td>
</tr>
<tr>
<td valign="top">

public new SACommand



</td>
<td valign="top">

 [SelectCommand](selectcommand-property-3c15c40.md) 



</td>
<td valign="top">

Specifies an SACommand that is used during Fill or FillSchema to obtain a result set from the database for copying into a DataSet.



</td>
</tr>
<tr>
<td valign="top">

public new DataTableMappingCollection



</td>
<td valign="top">

 [TableMappings](tablemappings-property-3c15cd8.md) 



</td>
<td valign="top">

Specifies a collection that provides the master mapping between a source table and a DataTable.



</td>
</tr>
<tr>
<td valign="top">

public override int



</td>
<td valign="top">

 [UpdateBatchSize](updatebatchsize-property-3c15e85.md) 



</td>
<td valign="top">

Gets or sets the number of rows that are processed in each round-trip to the database server.



</td>
</tr>
<tr>
<td valign="top">

public new SACommand



</td>
<td valign="top">

 [UpdateCommand](updatecommand-property-3c15f10.md) 



</td>
<td valign="top">

Specifies an SACommand that is executed against the database when the Update method is called to update rows in the database that correspond to updated rows in the DataSet.



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

public SARowUpdatedEventHandler



</td>
<td valign="top">

 [RowUpdated](rowupdated-event-3c157a7.md) 



</td>
<td valign="top">

Occurs during an update after a command is executed against the data source.



</td>
</tr>
<tr>
<td valign="top">

public SARowUpdatingEventHandler



</td>
<td valign="top">

 [RowUpdating](rowupdating-event-3c1585a.md) 



</td>
<td valign="top">

Occurs during an update before a command is executed against the data source.



</td>
</tr>
</table>



## Remarks

The System.Data.DataSet provides a way to work with data offline. The SADataAdapter provides methods to associate a DataSet with a set of SQL statements.

 *Implements:* IDbDataAdapter, IDataAdapter, ICloneable

For more information, see "Data access and manipulation".

