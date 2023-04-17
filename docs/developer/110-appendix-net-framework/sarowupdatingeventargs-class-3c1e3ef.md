<!-- loio3c1e3ef36c5f1014be1fd6b5d4e560be -->

# SARowUpdatingEventArgs Class

Provides data for the RowUpdating event.



Visual Basic
:   ```
Public NotInheritable Class SARowUpdatingEventArgs Inherits System.Data.Common.RowUpdatingEventArgs
```

C\#
:   ```
public sealed class SARowUpdatingEventArgs : System.Data.Common.RowUpdatingEventArgs
```



## Members

All members of SARowUpdatingEventArgs, including inherited members.

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

 [SARowUpdatingEventArgs\(DataRow, IDbCommand, StatementType, DataTableMapping\)](sarowupdatingeventargs-datarow-idbcommand-statementtype-datatablemapping-constructor-3c1e367.md) 



</td>
<td valign="top">

Initializes a new instance of the SARowUpdatingEventArgs class.



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

 [Command](command-property-3c1e2ea.md) 



</td>
<td valign="top">

Specifies the SACommand to execute when performing the Update.



</td>
</tr>
</table>

