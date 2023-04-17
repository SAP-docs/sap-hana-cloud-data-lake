<!-- loio13e47ad9748d4d4d9536a0518b8ecd67 -->

# connect\(\{String | Object\}\[, Function\]\) Method

Creates a new connection to the database by using a connection string or a hash of connection parameters that is passed in as a parameter.



```
connection.connect(conn_params[, callback])
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

String or Object



</td>
<td valign="top">

`conn_params`



</td>
<td valign="top">

A valid connection string or a hash of connection parameters.



</td>
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

Before the end of the program, call the disconnect method to free up resources.

The charset \(CS\) connection parameter CS=UTF-8 is always appended to the end of the connection string by the driver since all strings must be sent in that encoding.

This method can be synchronous or asynchronous. Specify a callback function to use this method asynchronously. The callback function is of the form:

```js
function(err)
    {
    };
```



The following example shows how to use the connect method synchronously.

```js
var iq=require('@sap/iq-client');
    var client=iq.createConnection();
    client.connect("host=XXX-XXX.iq.hdl.trial-us10.hanacloud.ondemand.com:443;uid=XXXXXXX;pwd=XXXXXXXX;enc='TLS{tls_type=rsa;direct=yes}");
```

