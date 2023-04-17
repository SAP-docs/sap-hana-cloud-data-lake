<!-- loio3c19ebe86c5f1014a63bfc7a4ddbd038 -->

# SAInfoMessageEventArgs Class

Provides data for the InfoMessage event.



Visual Basic
:   ```
Public NotInheritable Class SAInfoMessageEventArgs Inherits System.EventArgs
```

C\#
:   ```
public sealed class SAInfoMessageEventArgs : System.EventArgs
```



## Members

All members of SAInfoMessageEventArgs, including inherited members.

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

 [ToString\(\)](tostring-method-3c19e3c.md) 



</td>
<td valign="top">

Retrieves a string representation of the InfoMessage event.



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

public SAErrorCollection



</td>
<td valign="top">

 [Errors](errors-property-3c19b47.md) 



</td>
<td valign="top">

Returns the collection of messages sent from the data source.



</td>
</tr>
<tr>
<td valign="top">

public string



</td>
<td valign="top">

 [Message](message-property-3c19bc9.md) 



</td>
<td valign="top">

Returns the full text of the error sent from the data source.



</td>
</tr>
<tr>
<td valign="top">

public SAMessageType



</td>
<td valign="top">

 [MessageType](messagetype-property-3c19c44.md) 



</td>
<td valign="top">

Returns the type of the message.



</td>
</tr>
<tr>
<td valign="top">

public int



</td>
<td valign="top">

 [NativeError](nativeerror-property-3c19cc4.md) 



</td>
<td valign="top">

Returns the SQLCODE returned by the database.



</td>
</tr>
<tr>
<td valign="top">

public string



</td>
<td valign="top">

 [Source](source-property-3c19dc1.md) 



</td>
<td valign="top">

Returns the name of the .NET Data Provider.



</td>
</tr>
</table>



## Remarks

There is no constructor for SAInfoMessageEventArgs.

