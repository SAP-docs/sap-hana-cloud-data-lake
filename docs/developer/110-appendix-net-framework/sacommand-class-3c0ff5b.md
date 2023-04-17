<!-- loio3c0ff5b76c5f10148352aa573b2bc242 -->

# SACommand Class

A SQL statement or stored procedure that is executed against a database.



Visual Basic
:   ```
Public NotInheritable Class SACommand Inherits System.Data.Common.DbCommand Implements System.ICloneable
```

C\#
:   ```
public sealed class SACommand : System.Data.Common.DbCommand, System.ICloneable
```



## Members

All members of SACommand, including inherited members.

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

 [SACommand](sacommand-constructor-3c0fddf.md) 



</td>
<td valign="top">

Initializes an SACommand object.



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

public IAsyncResult



</td>
<td valign="top">

 [BeginExecuteNonQuery](beginexecutenonquery-method-3c0ea3f.md) 



</td>
<td valign="top">

Initiates the asynchronous execution of a SQL statement or stored procedure that is described by this SACommand.



</td>
</tr>
<tr>
<td valign="top">

public IAsyncResult



</td>
<td valign="top">

 [BeginExecuteReader](beginexecutereader-method-3c0eca2.md) 



</td>
<td valign="top">

Initiates the asynchronous execution of a SQL statement or stored procedure that is described by this SACommand, and retrieves one or more result sets from the database server.



</td>
</tr>
<tr>
<td valign="top">

public override void



</td>
<td valign="top">

 [Cancel\(\)](cancel-method-3c0ed1c.md) 



</td>
<td valign="top">

Cancels the execution of an SACommand object.



</td>
</tr>
<tr>
<td valign="top">

protected override DbParameter



</td>
<td valign="top">

 [CreateDbParameter\(\)](createdbparameter-method-3c0ef82.md) 



</td>
<td valign="top">

Creates a new instance of a System.Data.Common.DbParameter object.



</td>
</tr>
<tr>
<td valign="top">

public new SAParameter



</td>
<td valign="top">

 [CreateParameter\(\)](createparameter-method-3c0f000.md) 



</td>
<td valign="top">

Provides an SAParameter object for supplying parameters to SACommand objects.



</td>
</tr>
<tr>
<td valign="top">

protected override void



</td>
<td valign="top">

 [Dispose\(bool\)](dispose-bool-method-3c0f377.md) 



</td>
<td valign="top">

Frees the resources associated with the object.



</td>
</tr>
<tr>
<td valign="top">

public unsafe int



</td>
<td valign="top">

 [EndExecuteNonQuery\(IAsyncResult\)](endexecutenonquery-iasyncresult-method-3c0f3f9.md) 



</td>
<td valign="top">

Finishes asynchronous execution of a SQL statement or stored procedure.



</td>
</tr>
<tr>
<td valign="top">

public unsafe SADataReader



</td>
<td valign="top">

 [EndExecuteReader\(IAsyncResult\)](endexecutereader-iasyncresult-method-3c0f477.md) 



</td>
<td valign="top">

Finishes asynchronous execution of a SQL statement or stored procedure, returning the requested SADataReader.



</td>
</tr>
<tr>
<td valign="top">

protected override DbDataReader



</td>
<td valign="top">

 [ExecuteDbDataReader\(CommandBehavior\)](executedbdatareader-commandbehavior-method-3c0f4f4.md) 



</td>
<td valign="top">

Executes the command text against the connection.



</td>
</tr>
<tr>
<td valign="top">

public override unsafe int



</td>
<td valign="top">

 [ExecuteNonQuery\(\)](executenonquery-method-3c0f56f.md) 



</td>
<td valign="top">

Executes a statement that does not return a result set, such as an INSERT, UPDATE, DELETE, or data definition statement.



</td>
</tr>
<tr>
<td valign="top">

public new SADataReader



</td>
<td valign="top">

 [ExecuteReader](executereader-method-3c0f6e6.md) 



</td>
<td valign="top">

Executes a SQL statement that returns a result set.



</td>
</tr>
<tr>
<td valign="top">

public new Task< SADataReader \>



</td>
<td valign="top">

 [ExecuteReaderAsync](executereaderasync-method-81df80d.md) 



</td>
<td valign="top">

An asynchronous version of SACommand.ExecuteReader, which Executes a SQL statement that returns a result set.



</td>
</tr>
<tr>
<td valign="top">

public override object



</td>
<td valign="top">

 [ExecuteScalar\(\)](executescalar-method-3c0f7de.md) 



</td>
<td valign="top">

Executes a statement that returns a single value.



</td>
</tr>
<tr>
<td valign="top">

public override void



</td>
<td valign="top">

 [Prepare\(\)](prepare-method-3c0f953.md) 



</td>
<td valign="top">

Prepares or compiles the SACommand on the data source.



</td>
</tr>
<tr>
<td valign="top">

public void



</td>
<td valign="top">

 [ResetCommandTimeout\(\)](resetcommandtimeout-method-3c0fa70.md) 



</td>
<td valign="top">

Resets the CommandTimeout property to its default value of 30 seconds.



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

public override string



</td>
<td valign="top">

 [CommandText](commandtext-property-3c0ed95.md) 



</td>
<td valign="top">

Gets or sets the text of a SQL statement or stored procedure.



</td>
</tr>
<tr>
<td valign="top">

public override int



</td>
<td valign="top">

 [CommandTimeout](commandtimeout-property-3c0ee18.md) 



</td>
<td valign="top">

This feature is not supported by the .NET Data Provider.



</td>
</tr>
<tr>
<td valign="top">

public override CommandType



</td>
<td valign="top">

 [CommandType](commandtype-property-3c0ee91.md) 



</td>
<td valign="top">

Gets or sets the type of command represented by an SACommand.



</td>
</tr>
<tr>
<td valign="top">

public new SAConnection



</td>
<td valign="top">

 [Connection](connection-property-3c0ef0a.md) 



</td>
<td valign="top">

Gets or sets the connection object to which the SACommand object applies.



</td>
</tr>
<tr>
<td valign="top">

protected override DbConnection



</td>
<td valign="top">

 [DbConnection](dbconnection-property-3c0f178.md) 



</td>
<td valign="top">

Gets or sets the System.Data.Common.DbConnection used by this SACommand object.



</td>
</tr>
<tr>
<td valign="top">

protected override DbParameterCollection



</td>
<td valign="top">

 [DbParameterCollection](dbparametercollection-property-3c0f1f9.md) 



</td>
<td valign="top">

Gets the collection of System.Data.Common.DbParameter objects.



</td>
</tr>
<tr>
<td valign="top">

protected override DbTransaction



</td>
<td valign="top">

 [DbTransaction](dbtransaction-property-3c0f27e.md) 



</td>
<td valign="top">

Gets or sets the System.Data.Common.DbTransaction within which this SACommand object executes.



</td>
</tr>
<tr>
<td valign="top">

public override bool



</td>
<td valign="top">

 [DesignTimeVisible](designtimevisible-property-3c0f2f9.md) 



</td>
<td valign="top">

Gets or sets a value that indicates if the SACommand should be visible in a Windows Form Designer control.



</td>
</tr>
<tr>
<td valign="top">

public new SAParameterCollection



</td>
<td valign="top">

 [Parameters](parameters-property-3c0f8d4.md) 



</td>
<td valign="top">

Specifies a collection of parameters for the current statement.



</td>
</tr>
<tr>
<td valign="top">

public new SATransaction



</td>
<td valign="top">

 [Transaction](transaction-property-3c0fe5b.md) 



</td>
<td valign="top">

Specifies the SATransaction object in which the SACommand executes.



</td>
</tr>
<tr>
<td valign="top">

public override UpdateRowSource



</td>
<td valign="top">

 [UpdatedRowSource](updatedrowsource-property-3c0fed9.md) 



</td>
<td valign="top">

Gets or sets how command results are applied to the DataRow when used by the Update method of the SADataAdapter.



</td>
</tr>
</table>



## Remarks

 *Implements:* IDbCommand, ICloneable

For more information, see "Data access and manipulation".

