<!-- loio3c1de11f6c5f1014be92b979a232efbd -->

# SAPermissionAttribute Class

Associates a security action with a custom security attribute.



Visual Basic
:   ```
Public NotInheritable Class SAPermissionAttribute Inherits System.Data.Common.DBDataPermissionAttribute
```

C\#
:   ```
public sealed class SAPermissionAttribute : System.Data.Common.DBDataPermissionAttribute
```



## Members

All members of SAPermissionAttribute, including inherited members.

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

 [SAPermissionAttribute\(SecurityAction\)](sapermissionattribute-securityaction-constructor-3c1dd98.md) 



</td>
<td valign="top">

Initializes a new instance of the SAPermissionAttribute class.



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

public override IPermission



</td>
<td valign="top">

 [CreatePermission\(\)](createpermission-method-3c1dd1a.md) 



</td>
<td valign="top">

Returns an SAPermission object that is configured according to the attribute properties.



</td>
</tr>
</table>

