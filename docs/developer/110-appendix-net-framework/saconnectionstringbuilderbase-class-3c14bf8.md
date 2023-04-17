<!-- loio3c14bf846c5f1014a6f18f4887c51550 -->

# SAConnectionStringBuilderBase Class

Base class of the SAConnectionStringBuilder class.



Visual Basic
:   ```
Public MustInherit Class SAConnectionStringBuilderBase Inherits System.Data.Common.DbConnectionStringBuilder
```

C\#
:   ```
public abstract class SAConnectionStringBuilderBase : System.Data.Common.DbConnectionStringBuilder
```



## Members

All members of SAConnectionStringBuilderBase, including inherited members.

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

public override bool



</td>
<td valign="top">

 [ContainsKey\(string\)](containskey-string-method-3c142a1.md) 



</td>
<td valign="top">

Determines whether the SAConnectionStringBuilder object contains a specific keyword.



</td>
</tr>
<tr>
<td valign="top">

public string



</td>
<td valign="top">

 [GetKeyword\(string\)](getkeyword-string-method-3c145ae.md) 



</td>
<td valign="top">

Gets the keyword for the specified SAConnectionStringBuilder property.



</td>
</tr>
<tr>
<td valign="top">

public bool



</td>
<td valign="top">

 [GetUseLongNameAsKeyword\(\)](getuselongnameaskeyword-method-3c146ac.md) 



</td>
<td valign="top">

Gets a boolean value that indicates whether long connection parameter names are used in the connection string.



</td>
</tr>
<tr>
<td valign="top">

public override bool



</td>
<td valign="top">

 [Remove\(string\)](remove-string-method-3c14899.md) 



</td>
<td valign="top">

Removes the entry with the specified key from the SAConnectionStringBuilder instance.



</td>
</tr>
<tr>
<td valign="top">

public void



</td>
<td valign="top">

 [SetUseLongNameAsKeyword\(bool\)](setuselongnameaskeyword-bool-method-3c14a0f.md) 



</td>
<td valign="top">

Sets a boolean value that indicates whether long connection parameter names are used in the connection string.



</td>
</tr>
<tr>
<td valign="top">

public override bool



</td>
<td valign="top">

 [ShouldSerialize\(string\)](shouldserialize-string-method-3c14a8b.md) 



</td>
<td valign="top">

Indicates whether the specified key exists in this SAConnectionStringBuilder instance.



</td>
</tr>
<tr>
<td valign="top">

public override bool



</td>
<td valign="top">

 [TryGetValue\(string, out object\)](trygetvalue-string-out-object-method-3c14b80.md) 



</td>
<td valign="top">

Retrieves a value corresponding to the supplied key from this SAConnectionStringBuilder.



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

public override ICollection



</td>
<td valign="top">

 [Keys](keys-property-3c1472d.md) 



</td>
<td valign="top">

Gets an System.Collections.ICollection that contains the keys in the SAConnectionStringBuilder.



</td>
</tr>
<tr>
<td valign="top">

public override object



</td>
<td valign="top">

 [this\[string keyword\]](this-string-keyword-property-3c14b04.md) 



</td>
<td valign="top">

Gets or sets the value of the connection keyword.



</td>
</tr>
</table>

