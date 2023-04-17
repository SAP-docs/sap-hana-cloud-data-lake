<!-- loio3c194e656c5f1014ad2fe570f65582bc -->

# SAException Class

The exception that is thrown when the database server returns a warning or error.



Visual Basic
:   ```
Public Class SAException Inherits System.Exception
```

C\#
:   ```
public class SAException : System.Exception
```



## Members

All members of SAException, including inherited members.

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

public override void



</td>
<td valign="top">

 [GetObjectData\(SerializationInfo, StreamingContext\)](getobjectdata-serializationinfo-streamingcontext-method-3c191ec.md) 



</td>
<td valign="top">

Sets the SerializationInfo with information about the exception.



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

 [Errors](errors-property-3c190e1.md) 



</td>
<td valign="top">

Returns a collection of one or more SAError objects.



</td>
</tr>
<tr>
<td valign="top">

public override string



</td>
<td valign="top">

 [Message](message-property-3c1931a.md) 



</td>
<td valign="top">

Returns the text describing the error.



</td>
</tr>
<tr>
<td valign="top">

public int



</td>
<td valign="top">

 [NativeError](nativeerror-property-3c193bd.md) 



</td>
<td valign="top">

Returns database-specific error information.



</td>
</tr>
<tr>
<td valign="top">

public override string



</td>
<td valign="top">

 [Source](source-property-3c19463.md) 



</td>
<td valign="top">

Returns the name of the provider that generated the error.



</td>
</tr>
</table>



## Remarks

There is no constructor for SAException. Typically, an SAException object is declared in a catch. For example:

```
...
catch( SAException ex )
{
   MessageBox.Show( ex.Errors[0].Message, "Error" );
}
```

For information about error handling, see ".NET error handling".

