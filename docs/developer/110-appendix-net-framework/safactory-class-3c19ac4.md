<!-- loio3c19ac426c5f1014a662b45d98066041 -->

# SAFactory Class

Represents a set of methods for creating instances of the Sap.Data.SQLAnywhere provider's implementation of the data source classes.



Visual Basic
:   ```
Public NotInheritable Class SAFactory Inherits System.Data.Common.DbProviderFactory
```

C\#
:   ```
public sealed class SAFactory : System.Data.Common.DbProviderFactory
```



## Members

All members of SAFactory, including inherited members.

 **Variables** 


<table>
<tr>
<th valign="top">

Modifier and Type



</th>
<th valign="top">

Variable



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

public static readonly SAFactory



</td>
<td valign="top">

Instance



</td>
<td valign="top">

Represents the singleton instance of the SAFactory class.

SAFactory is a singleton class, which means only this instance of this class can exist.

Normally you would not use this field directly. Instead, you get a reference to this instance of SAFactory using System.Data.Common.DbProviderFactories.GetFactory\(String\). For an example, see the SAFactory description.



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

public override DbCommand



</td>
<td valign="top">

 [CreateCommand\(\)](createcommand-method-3c195fe.md) 



</td>
<td valign="top">

Returns a strongly typed System.Data.Common.DbCommand instance.



</td>
</tr>
<tr>
<td valign="top">

public override DbCommandBuilder



</td>
<td valign="top">

 [CreateCommandBuilder\(\)](createcommandbuilder-method-3c19687.md) 



</td>
<td valign="top">

Returns a strongly typed System.Data.Common.DbCommandBuilder instance.



</td>
</tr>
<tr>
<td valign="top">

public override DbConnection



</td>
<td valign="top">

 [CreateConnection\(\)](createconnection-method-3c19701.md) 



</td>
<td valign="top">

Returns a strongly typed System.Data.Common.DbConnection instance.



</td>
</tr>
<tr>
<td valign="top">

public override DbConnectionStringBuilder



</td>
<td valign="top">

 [CreateConnectionStringBuilder\(\)](createconnectionstringbuilder-method-3c19789.md) 



</td>
<td valign="top">

Returns a strongly typed System.Data.Common.DbConnectionStringBuilder instance.



</td>
</tr>
<tr>
<td valign="top">

public override DbDataAdapter



</td>
<td valign="top">

 [CreateDataAdapter\(\)](createdataadapter-method-3c19809.md) 



</td>
<td valign="top">

Returns a strongly typed System.Data.Common.DbDataAdapter instance.



</td>
</tr>
<tr>
<td valign="top">

public override DbDataSourceEnumerator



</td>
<td valign="top">

 [CreateDataSourceEnumerator\(\)](createdatasourceenumerator-method-3c1988c.md) 



</td>
<td valign="top">

Returns a strongly typed System.Data.Common.DbDataSourceEnumerator instance.



</td>
</tr>
<tr>
<td valign="top">

public override DbParameter



</td>
<td valign="top">

 [CreateParameter\(\)](createparameter-method-3c19946.md) 



</td>
<td valign="top">

Returns a strongly typed System.Data.Common.DbParameter instance.



</td>
</tr>
<tr>
<td valign="top">

public override CodeAccessPermission



</td>
<td valign="top">

 [CreatePermission\(PermissionState\)](createpermission-permissionstate-method-3c199c1.md) 



</td>
<td valign="top">

Returns a strongly-typed CodeAccessPermission instance.



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

public override bool



</td>
<td valign="top">

 [CanCreateDataSourceEnumerator](cancreatedatasourceenumerator-property-3c1957e.md) 



</td>
<td valign="top">

Always returns true, which indicates that an SADataSourceEnumerator object can be created.



</td>
</tr>
</table>



## Remarks

There is no constructor for SAFactory.

DbProviderFactories and DbProviderFactory make provider independent code easier to write. Specify Sap.Data.SQLAnywhere as the provider invariant name passed to GetFactory. For example:

```
' Visual Basic
Dim factory As DbProviderFactory = _
 DbProviderFactories.GetFactory( "Sap.Data.SQLAnywhere" )
Dim conn As DbConnection = _
 factory.CreateConnection()

// C#
DbProviderFactory factory = 
		DbProviderFactories.GetFactory("Sap.Data.SQLAnywhere" );
DbConnection conn = factory.CreateConnection();
```

In this example, conn is created as an SAConnection object.

For an explanation of provider factories and generic programming in ADO.NET, see [Generic Coding with the ADO.NET 2.0 Base Classes and Factories](http://msdn.microsoft.com/en-us/library/ms379620.aspx).

