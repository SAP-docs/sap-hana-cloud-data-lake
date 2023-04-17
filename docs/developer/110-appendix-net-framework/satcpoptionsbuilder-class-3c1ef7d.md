<!-- loio3c1ef7de6c5f1014829ad1030def33a0 -->

# SATcpOptionsBuilder Class

Provides a simple way to create and manage the TCP options portion of connection strings used by the SAConnection object.



Visual Basic
:   ```
Public NotInheritable Class SATcpOptionsBuilder Inherits SAConnectionStringBuilderBase
```

C\#
:   ```
public sealed class SATcpOptionsBuilder : SAConnectionStringBuilderBase
```



## Members

All members of SATcpOptionsBuilder, including inherited members.

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

 [SATcpOptionsBuilder](satcpoptionsbuilder-constructor-3c1ec1a.md) 



</td>
<td valign="top">

Initializes an SATcpOptionsBuilder object.



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

public override string



</td>
<td valign="top">

 [ToString\(\)](tostring-method-3c1ee87.md) 



</td>
<td valign="top">

Converts the SATcpOptionsBuilder object to a string representation.



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

 [Broadcast](broadcast-property-3c1e57a.md) 



</td>
<td valign="top">

Gets or sets the Broadcast option.



</td>
</tr>
<tr>
<td valign="top">

public string



</td>
<td valign="top">

 [BroadcastListener](broadcastlistener-property-3c1e610.md) 



</td>
<td valign="top">

Gets or sets the BroadcastListener option.



</td>
</tr>
<tr>
<td valign="top">

public string



</td>
<td valign="top">

 [ClientPort](clientport-property-3c1e6da.md) 



</td>
<td valign="top">

Gets or sets the ClientPort option.



</td>
</tr>
<tr>
<td valign="top">

public string



</td>
<td valign="top">

 [DoBroadcast](dobroadcast-property-3c1e79e.md) 



</td>
<td valign="top">

Gets or sets the DoBroadcast option.



</td>
</tr>
<tr>
<td valign="top">

public string



</td>
<td valign="top">

 [Host](host-property-3c1e829.md) 



</td>
<td valign="top">

Gets or sets the Host option.



</td>
</tr>
<tr>
<td valign="top">

public string



</td>
<td valign="top">

 [IPV6](ipv6-property-3c1e8aa.md) 



</td>
<td valign="top">

Gets or sets the IPV6 option.



</td>
</tr>
<tr>
<td valign="top">

public string



</td>
<td valign="top">

 [LocalOnly](localonly-property-3c1e9ad.md) 



</td>
<td valign="top">

Gets or sets the LocalOnly option.



</td>
</tr>
<tr>
<td valign="top">

public string



</td>
<td valign="top">

 [MyIP](myip-property-3c1ea28.md) 



</td>
<td valign="top">

Gets or sets the MyIP option.



</td>
</tr>
<tr>
<td valign="top">

public int



</td>
<td valign="top">

 [ReceiveBufferSize](receivebuffersize-property-3c1eaa5.md) 



</td>
<td valign="top">

Gets or sets the ReceiveBufferSize option.



</td>
</tr>
<tr>
<td valign="top">

public int



</td>
<td valign="top">

 [SendBufferSize](sendbuffersize-property-3c1ec9a.md) 



</td>
<td valign="top">

Gets or sets the Send BufferSize option.



</td>
</tr>
<tr>
<td valign="top">

public string



</td>
<td valign="top">

 [ServerPort](serverport-property-3c1ed17.md) 



</td>
<td valign="top">

Gets or sets the ServerPort option.



</td>
</tr>
<tr>
<td valign="top">

public string



</td>
<td valign="top">

 [TDS](tds-property-3c1ed91.md) 



</td>
<td valign="top">

Gets or sets the TDS option.



</td>
</tr>
<tr>
<td valign="top">

public int



</td>
<td valign="top">

 [Timeout](timeout-property-3c1ee0f.md) 



</td>
<td valign="top">

Gets or sets the Timeout option.



</td>
</tr>
<tr>
<td valign="top">

public string



</td>
<td valign="top">

 [VerifyServerName](verifyservername-property-3c1ef04.md) 



</td>
<td valign="top">

Gets or sets the VerifyServerName option.



</td>
</tr>
</table>

 **Inherited members from SAConnectionStringBuilderBase** 


<table>
<tr>
<th valign="top">

Modifier and Type



</th>
<th valign="top">

Member



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

public override object



</td>
<td valign="top">

 [this\[string keyword\]](this-string-keyword-property-3c14b04.md) 



</td>
<td valign="top">

Gets or sets the value of the connection keyword.



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

**Related Information**  


[SAConnection Class](saconnection-class-3c126bb.md "Represents a connection to a database.")

