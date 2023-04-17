<!-- loio3c126bb76c5f10148461f108c0beefc4 -->

# SAConnection Class

Represents a connection to a database.



Visual Basic
:   ```
Public NotInheritable Class SAConnection Inherits System.Data.Common.DbConnection
```

C\#
:   ```
public sealed class SAConnection : System.Data.Common.DbConnection
```



## Members

All members of SAConnection, including inherited members.

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

 [SAConnection](saconnection-constructor-3c1235f.md) 



</td>
<td valign="top">

Initializes an SAConnection object.



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

protected override DbTransaction



</td>
<td valign="top">

 [BeginDbTransaction\(IsolationLevel\)](begindbtransaction-isolationlevel-method-3c112b1.md) 



</td>
<td valign="top">

Starts a database transaction.



</td>
</tr>
<tr>
<td valign="top">

public new SATransaction



</td>
<td valign="top">

 [BeginTransaction](begintransaction-method-3c1149f.md) 



</td>
<td valign="top">

Returns a transaction object.



</td>
</tr>
<tr>
<td valign="top">

public override void



</td>
<td valign="top">

 [ChangeDatabase\(string\)](changedatabase-string-method-3c11523.md) 



</td>
<td valign="top">

Changes the current database for an open SAConnection.



</td>
</tr>
<tr>
<td valign="top">

public static void



</td>
<td valign="top">

 [ChangePassword\(string, string\)](changepassword-string-string-method-3c115a7.md) 



</td>
<td valign="top">

Changes the password to the supplied new password for the user indicated in the connection string.



</td>
</tr>
<tr>
<td valign="top">

public static void



</td>
<td valign="top">

 [ClearAllPools\(\)](clearallpools-method-3c11622.md) 



</td>
<td valign="top">

Empties all connection pools.



</td>
</tr>
<tr>
<td valign="top">

public static void



</td>
<td valign="top">

 [ClearPool\(SAConnection\)](clearpool-saconnection-method-3c116a1.md) 



</td>
<td valign="top">

Empties the connection pool associated with the specified connection.



</td>
</tr>
<tr>
<td valign="top">

public override void



</td>
<td valign="top">

 [Close\(\)](close-method-3c11733.md) 



</td>
<td valign="top">

Closes a database connection.



</td>
</tr>
<tr>
<td valign="top">

public new SACommand



</td>
<td valign="top">

 [CreateCommand\(\)](createcommand-method-3c118d8.md) 



</td>
<td valign="top">

Initializes an SACommand object.



</td>
</tr>
<tr>
<td valign="top">

protected override DbCommand



</td>
<td valign="top">

 [CreateDbCommand\(\)](createdbcommand-method-3c11979.md) 



</td>
<td valign="top">

Creates and returns a System.Data.Common.DbCommand object associated with the current connection.



</td>
</tr>
<tr>
<td valign="top">

protected override void



</td>
<td valign="top">

 [Dispose\(bool\)](dispose-bool-method-3c11b0e.md) 



</td>
<td valign="top">

Frees the resources associated with the object.



</td>
</tr>
<tr>
<td valign="top">

public void



</td>
<td valign="top">

 [EnlistDistributedTransaction\(System.EnterpriseServices.ITransaction\)](enlistdistributedtransaction-system-enterpriseservices-itransaction-method-3c11b91.md) 



</td>
<td valign="top">

Enlists in the specified transaction as a distributed transaction.



</td>
</tr>
<tr>
<td valign="top">

public override void



</td>
<td valign="top">

 [EnlistTransaction\(System.Transactions.Transaction\)](enlisttransaction-system-transactions-transaction-method-3c11c1e.md) 



</td>
<td valign="top">

Enlists in the specified transaction as a distributed transaction.



</td>
</tr>
<tr>
<td valign="top">

public override DataTable



</td>
<td valign="top">

 [GetSchema](getschema-method-3c11f87.md) 



</td>
<td valign="top">

Returns the list of supported schema collections.



</td>
</tr>
<tr>
<td valign="top">

public override unsafe void



</td>
<td valign="top">

 [Open\(\)](open-method-3c121f1.md) 



</td>
<td valign="top">

Opens a database connection with the property settings specified by the SAConnection.ConnectionString.



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

 [ConnectionString](connectionstring-property-3c117be.md) 



</td>
<td valign="top">

Provides the database connection string.



</td>
</tr>
<tr>
<td valign="top">

public override int



</td>
<td valign="top">

 [ConnectionTimeout](connectiontimeout-property-3c11853.md) 



</td>
<td valign="top">

Gets the number of seconds before a connection attempt times out with an error.



</td>
</tr>
<tr>
<td valign="top">

public SACredential



</td>
<td valign="top">

 [Credential](credential-property-81e1133.md) 



</td>
<td valign="top">

Gets or sets the SACredential object for this connection.



</td>
</tr>
<tr>
<td valign="top">

public override string



</td>
<td valign="top">

 [Database](database-property-3c119fd.md) 



</td>
<td valign="top">

Gets the name of the current database.



</td>
</tr>
<tr>
<td valign="top">

public override string



</td>
<td valign="top">

 [DataSource](datasource-property-3c11a7f.md) 



</td>
<td valign="top">

Gets the name of the database server.



</td>
</tr>
<tr>
<td valign="top">

public string



</td>
<td valign="top">

 [InitString](initstring-property-3c120f9.md) 



</td>
<td valign="top">

A command that is executed immediately after the connection is established.



</td>
</tr>
<tr>
<td valign="top">

public override string



</td>
<td valign="top">

 [ServerVersion](serverversion-property-3c12453.md) 



</td>
<td valign="top">

Gets a string that contains the version of the instance of the database server to which the client is connected.



</td>
</tr>
<tr>
<td valign="top">

public override ConnectionState



</td>
<td valign="top">

 [State](state-property-3c124d0.md) 



</td>
<td valign="top">

Indicates the state of the SAConnection object.



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

public SAInfoMessageEventHandler



</td>
<td valign="top">

 [InfoMessage](infomessage-event-3c1207c.md) 



</td>
<td valign="top">

Occurs when the database server returns a warning or informational message.



</td>
</tr>
<tr>
<td valign="top">

public override StateChangeEventHandler



</td>
<td valign="top">

 [StateChange](statechange-event-3c1254e.md) 



</td>
<td valign="top">

Occurs when the state of the SAConnection object changes.



</td>
</tr>
</table>



## Remarks

For a list of connection parameters, see ".NET connection parameters" and "Connection parameters".

