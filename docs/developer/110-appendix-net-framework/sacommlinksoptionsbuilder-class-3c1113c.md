<!-- loio3c1113c26c5f10149b37ab12ded2db25 -->

# SACommLinksOptionsBuilder Class

Provides a simple way to create and manage the CommLinks options portion of connection strings used by the SAConnection class.



Visual Basic
:   ```
Public NotInheritable Class SACommLinksOptionsBuilder
```

C\#
:   ```
public sealed class SACommLinksOptionsBuilder
```



## Members

All members of SACommLinksOptionsBuilder, including inherited members.

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

 [SACommLinksOptionsBuilder](sacommlinksoptionsbuilder-constructor-81e08aa.md) 



</td>
<td valign="top">

Initializes an SACommLinksOptionsBuilder object.



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

public bool



</td>
<td valign="top">

 [GetUseLongNameAsKeyword\(\)](getuselongnameaskeyword-method-3c10e52.md) 



</td>
<td valign="top">

Gets a boolean value that indicates whether long connection parameter names are used in the connection string.



</td>
</tr>
<tr>
<td valign="top">

public void



</td>
<td valign="top">

 [SetUseLongNameAsKeyword\(bool\)](setuselongnameaskeyword-bool-method-3c10ecc.md) 



</td>
<td valign="top">

Sets a boolean value that indicates whether long connection parameter names are used in the connection string.



</td>
</tr>
<tr>
<td valign="top">

public override string



</td>
<td valign="top">

 [ToString\(\)](tostring-method-3c110c0.md) 



</td>
<td valign="top">

Converts the SACommLinksOptionsBuilder object to a string representation.



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

public bool



</td>
<td valign="top">

 [All](all-property-3c10d4f.md) 



</td>
<td valign="top">

Gets or sets the ALL CommLinks option.



</td>
</tr>
<tr>
<td valign="top">

public string



</td>
<td valign="top">

 [ConnectionString](connectionstring-property-3c10dd0.md) 



</td>
<td valign="top">

Gets or sets the connection string being built.



</td>
</tr>
<tr>
<td valign="top">

public bool



</td>
<td valign="top">

 [SharedMemory](sharedmemory-property-3c10f4a.md) 



</td>
<td valign="top">

Gets or sets the SharedMemory protocol.



</td>
</tr>
<tr>
<td valign="top">

public SATcpOptionsBuilder



</td>
<td valign="top">

 [TcpOptionsBuilder](tcpoptionsbuilder-property-3c10fc5.md) 



</td>
<td valign="top">

Gets or sets an SATcpOptionsBuilder object used to create a TCP options string.



</td>
</tr>
<tr>
<td valign="top">

public string



</td>
<td valign="top">

 [TcpOptionsString](tcpoptionsstring-property-3c11046.md) 



</td>
<td valign="top">

Gets or sets a string of TCP options.



</td>
</tr>
</table>



## Remarks

For a list of connection parameters, see "Connection parameters".

