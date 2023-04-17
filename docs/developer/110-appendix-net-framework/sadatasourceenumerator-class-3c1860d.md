<!-- loio3c1860d66c5f1014aadaf241b731c951 -->

# SADataSourceEnumerator Class

Provides a mechanism for enumerating all available instances of database servers within the local network.



Visual Basic
:   ```
Public NotInheritable Class SADataSourceEnumerator Inherits System.Data.Common.DbDataSourceEnumerator
```

C\#
:   ```
public sealed class SADataSourceEnumerator : System.Data.Common.DbDataSourceEnumerator
```



## Members

All members of SADataSourceEnumerator, including inherited members.

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

public unsafe override DataTable



</td>
<td valign="top">

 [GetDataSources\(\)](getdatasources-method-3c1849d.md) 



</td>
<td valign="top">

Retrieves a DataTable containing information about all visible database servers.



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

public SADataSourceEnumerator



</td>
<td valign="top">

 [Instance](instance-property-3c1851a.md) 



</td>
<td valign="top">

Gets an instance of SADataSourceEnumerator, which can be used to retrieve information about all visible database servers.



</td>
</tr>
</table>



## Remarks

There is no constructor for SADataSourceEnumerator.

