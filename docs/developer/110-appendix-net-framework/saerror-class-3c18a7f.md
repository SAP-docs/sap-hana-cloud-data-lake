<!-- loio3c18a7f36c5f1014a3d19c14d706c647 -->

# SAError Class

Collects information relevant to a warning or error returned by the data source.



Visual Basic
:   ```
Public NotInheritable Class SAError
```

C\#
:   ```
public sealed class SAError
```



## Members

All members of SAError, including inherited members.

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

public override string



</td>
<td valign="top">

 [ToString\(\)](tostring-method-3c18a00.md) 



</td>
<td valign="top">

The complete text of the error message.



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

public string



</td>
<td valign="top">

 [Message](message-property-3c18782.md) 



</td>
<td valign="top">

Returns a short description of the error.



</td>
</tr>
<tr>
<td valign="top">

public int



</td>
<td valign="top">

 [NativeError](nativeerror-property-3c1880c.md) 



</td>
<td valign="top">

Returns database-specific error information.



</td>
</tr>
<tr>
<td valign="top">

public string



</td>
<td valign="top">

 [Source](source-property-3c18906.md) 



</td>
<td valign="top">

Returns the name of the provider that generated the error.



</td>
</tr>
<tr>
<td valign="top">

public string



</td>
<td valign="top">

 [SqlState](sqlstate-property-3c18985.md) 



</td>
<td valign="top">

The five-character SQLSTATE following the ANSI SQL standard.



</td>
</tr>
</table>



## Remarks

There is no constructor for SAError.

For information about error handling, see ".NET error handling".

