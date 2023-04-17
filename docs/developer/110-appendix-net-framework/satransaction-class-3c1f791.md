<!-- loio3c1f79156c5f1014b95fe321880f9766 -->

# SATransaction Class

Represents a SQL transaction.



Visual Basic
:   ```
Public NotInheritable Class SATransaction Inherits System.Data.Common.DbTransaction
```

C\#
:   ```
public sealed class SATransaction : System.Data.Common.DbTransaction
```



## Members

All members of SATransaction, including inherited members.

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

public override void



</td>
<td valign="top">

 [Commit\(\)](commit-method-3c1eff8.md) 



</td>
<td valign="top">

Commits the database transaction.



</td>
</tr>
<tr>
<td valign="top">

protected override void



</td>
<td valign="top">

 [Dispose\(bool\)](dispose-bool-method-3c1f269.md) 



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

public override void



</td>
<td valign="top">

 [Rollback](rollback-method-3c1f517.md) 



</td>
<td valign="top">

Rolls back a transaction from a pending state.



</td>
</tr>
<tr>
<td valign="top">

public unsafe void



</td>
<td valign="top">

 [Save\(string\)](save-string-method-3c1f612.md) 



</td>
<td valign="top">

Creates a savepoint in the transaction that can be used to roll back a portion of the transaction, and specifies the savepoint name.



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

public new SAConnection



</td>
<td valign="top">

 [Connection](connection-property-3c1f074.md) 



</td>
<td valign="top">

The SAConnection object associated with the transaction, or a null reference \(Nothing in Visual Basic\) if the transaction is no longer valid.



</td>
</tr>
<tr>
<td valign="top">

protected override DbConnection



</td>
<td valign="top">

 [DbConnection](dbconnection-property-3c1f1ec.md) 



</td>
<td valign="top">

Specifies the System.Data.Common.DbConnection object associated with the transaction.



</td>
</tr>
<tr>
<td valign="top">

public override System.Data.IsolationLevel



</td>
<td valign="top">

 [IsolationLevel](isolationlevel-property-3c1f2f6.md) 



</td>
<td valign="top">

Specifies the isolation level for this transaction.



</td>
</tr>
<tr>
<td valign="top">

public SAIsolationLevel



</td>
<td valign="top">

 [SAIsolationLevel](saisolationlevel-property-3c1f591.md) 



</td>
<td valign="top">

Specifies the extended isolation level for this transaction.



</td>
</tr>
</table>



## Remarks

There is no constructor for SATransaction. To obtain an SATransaction object, use one of the BeginTransaction methods. To associate a command with a transaction, use the SACommand.Transaction property.

For more information, see "Transaction processing" and "Data access and manipulation".

**Related Information**  


[BeginTransaction\(\) Method](begintransaction-method-3c11328.md "Returns a transaction object.")

[BeginTransaction\(SAIsolationLevel\) Method](begintransaction-saisolationlevel-method-3c11421.md "Returns a transaction object.")

[Transaction Property](transaction-property-3c0fe5b.md "Specifies the SATransaction object in which the SACommand executes.")

