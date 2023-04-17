<!-- loio3c1e26c46c5f10149513acdf84281a19 -->

# SARowUpdatedEventArgs Class

Provides data for the RowUpdated event.



Visual Basic
:   ```
Public NotInheritable Class SARowUpdatedEventArgs Inherits System.Data.Common.RowUpdatedEventArgs
```

C\#
:   ```
public sealed class SARowUpdatedEventArgs : System.Data.Common.RowUpdatedEventArgs
```



## Members

All members of SARowUpdatedEventArgs, including inherited members.

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

 [SARowUpdatedEventArgs\(DataRow, IDbCommand, StatementType, DataTableMapping\)](sarowupdatedeventargs-datarow-idbcommand-statementtype-datatablemapping-constructor-3c1e1f4.md) 



</td>
<td valign="top">

Initializes a new instance of the SARowUpdatedEventArgs class.



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

 [Command](command-property-3c1e080.md) 



</td>
<td valign="top">

Gets the SACommand that is executed when DataAdapter.Update is called.



</td>
</tr>
<tr>
<td valign="top">

public new int



</td>
<td valign="top">

 [RecordsAffected](recordsaffected-property-3c1e177.md) 



</td>
<td valign="top">

Returns the number of rows changed, inserted, or deleted by the execution of the SQL statement.



</td>
</tr>
</table>

