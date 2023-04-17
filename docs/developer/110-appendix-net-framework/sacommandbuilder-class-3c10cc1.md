<!-- loio3c10cc1e6c5f1014865ea0555a988d4f -->

# SACommandBuilder Class

A way to generate single-table SQL statements that reconcile changes made to a DataSet with the data in the associated database.



Visual Basic
:   ```
Public NotInheritable Class SACommandBuilder Inherits System.Data.Common.DbCommandBuilder
```

C\#
:   ```
public sealed class SACommandBuilder : System.Data.Common.DbCommandBuilder
```



## Members

All members of SACommandBuilder, including inherited members.

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

 [SACommandBuilder](sacommandbuilder-constructor-3c10b4d.md) 



</td>
<td valign="top">

Initializes an SACommandBuilder object.



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

 [ApplyParameterInfo\(DbParameter, DataRow, StatementType, bool\)](applyparameterinfo-dbparameter-datarow-statementtype-bool-method-3c0ffe3.md) 



</td>
<td valign="top">

Allows the provider implementation of System.Data.Common.DbCommandBuilder to handle additional parameter properties.



</td>
</tr>
<tr>
<td valign="top">

public static void



</td>
<td valign="top">

 [DeriveParameters\(SACommand\)](deriveparameters-sacommand-method-3c1015c.md) 



</td>
<td valign="top">

Populates the Parameters collection of the specified SACommand object.



</td>
</tr>
<tr>
<td valign="top">

public new SACommand



</td>
<td valign="top">

 [GetDeleteCommand](getdeletecommand-method-3c102d6.md) 



</td>
<td valign="top">

Returns the generated SACommand object that performs DELETE operations on the database when SADataAdapter.Update is called.



</td>
</tr>
<tr>
<td valign="top">

public new SACommand



</td>
<td valign="top">

 [GetInsertCommand](getinsertcommand-method-3c1044d.md) 



</td>
<td valign="top">

Returns the generated SACommand object that performs INSERT operations on the database when an Update is called.



</td>
</tr>
<tr>
<td valign="top">

protected override string



</td>
<td valign="top">

 [GetParameterName](getparametername-method-3c105be.md) 



</td>
<td valign="top">

Returns the name of the specified parameter in the format of @p\#.



</td>
</tr>
<tr>
<td valign="top">

protected override string



</td>
<td valign="top">

 [GetParameterPlaceholder\(int\)](getparameterplaceholder-int-method-3c1063c.md) 



</td>
<td valign="top">

Returns the placeholder for the parameter in the associated SQL statement.



</td>
</tr>
<tr>
<td valign="top">

protected override DataTable



</td>
<td valign="top">

 [GetSchemaTable\(DbCommand\)](getschematable-dbcommand-method-3c106bb.md) 



</td>
<td valign="top">

Returns the schema table for the SACommandBuilder object.



</td>
</tr>
<tr>
<td valign="top">

public new SACommand



</td>
<td valign="top">

 [GetUpdateCommand](getupdatecommand-method-3c10835.md) 



</td>
<td valign="top">

Returns the generated SACommand object that performs UPDATE operations on the database when an Update is called.



</td>
</tr>
<tr>
<td valign="top">

protected override DbCommand



</td>
<td valign="top">

 [InitializeCommand\(DbCommand\)](initializecommand-dbcommand-method-3c108b1.md) 



</td>
<td valign="top">

Resets the System.Data.Common.DbCommand.CommandTimeout, System.Data.Common.DbCommand.Transaction, System.Data.Common.DbCommand.CommandType, and System.Data.Common.DbCommand.UpdatedRowSource properties on the System.Data.Common.DbCommand.



</td>
</tr>
<tr>
<td valign="top">

public override string



</td>
<td valign="top">

 [QuoteIdentifier\(string\)](quoteidentifier-string-method-3c10942.md) 



</td>
<td valign="top">

Returns the correct quoted form of an unquoted identifier, including properly escaping any embedded quotes in the identifier.



</td>
</tr>
<tr>
<td valign="top">

protected override void



</td>
<td valign="top">

 [SetRowUpdatingHandler\(DbDataAdapter\)](setrowupdatinghandler-dbdataadapter-method-3c10bca.md) 



</td>
<td valign="top">

Registers the SACommandBuilder object to handle the SADataAdapter.RowUpdating event for an SADataAdapter object.



</td>
</tr>
<tr>
<td valign="top">

public override string



</td>
<td valign="top">

 [UnquoteIdentifier\(string\)](unquoteidentifier-string-method-3c10c45.md) 



</td>
<td valign="top">

Returns the correct unquoted form of a quoted identifier, including properly un-escaping any embedded quotes in the identifier.



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

public new SADataAdapter



</td>
<td valign="top">

 [DataAdapter](dataadapter-property-3c100e0.md) 



</td>
<td valign="top">

Specifies the SADataAdapter for which to generate statements.



</td>
</tr>
</table>

