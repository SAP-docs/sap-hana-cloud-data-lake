<!-- loio3c18708a6c5f1014bc39869a4989fd7f -->

# SADefault Class

Represents a parameter with a default value.



Visual Basic
:   ```
Public NotInheritable Class SADefault
```

C\#
:   ```
public sealed class SADefault
```



## Members

All members of SADefault, including inherited members.

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

public static readonly SADefault



</td>
<td valign="top">

Value



</td>
<td valign="top">

Gets the value for a default parameter.

This field is read-only and static.



</td>
</tr>
</table>



## Remarks

There is no constructor for SADefault.

```
SAParameter parm = new SAParameter();
parm.Value = SADefault.Value;
```

