<!-- loio8dee077765f5476b8b481ab1de864f14 -->

# \{disconnect | close | end\}\(\[Function\]\) Method

Closes the current connection.



```
connection.{disconnect | close | end}([callback])
```



## Parameters


<table>
<tr>
<th valign="top">

Type



</th>
<th valign="top">

Name



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

Function



</td>
<td valign="top">

`callback`



</td>
<td valign="top">

The optional callback function.



</td>
</tr>
</table>



## Remarks

Call this method before the program ends to free up resources.

This method can be synchronous or asynchronous. Specify a callback function to use this method asynchronously. The callback function is of the form:

```js
function(err)
    {
    };
```



The following examples shows how to use the disconnect method synchronously.

```js
var iq=require('@sap/iq-client');
    var client=iq.createConnection();
    client.connect("host=XXX-XXX.iq.hdl.trial-us10.hanacloud.ondemand.com:443;uid=XXXXXXX;pwd=XXXXXXXX;enc='TLS{tls_type=rsa;direct=yes}");
    client.disconnect();
```

**Related Information**  


[connect\(\{String | Object\}\[, Function\]\) Method](connect-string-object-function-method-13e47ad.md "Creates a new connection to the database by using a connection string or a hash of connection parameters that is passed in as a parameter.")

