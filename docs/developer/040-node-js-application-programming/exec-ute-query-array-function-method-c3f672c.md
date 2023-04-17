<!-- loioc3f672c31c4c4d5ea78c80a40a8247c9 -->

# exec\[ute\]Query\(\[Array\]\[, Function\]\) Method

Executes the prepared SQL statement and returns a result set object.



```
statement.exec[ute]Query ([params][, callback])
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

Array



</td>
<td valign="top">

`params`



</td>
<td valign="top">

Specifies an optional array of bind parameters to execute.



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

Specifies the optional callback function.



</td>
</tr>
</table>



## Returns

The result set object is returned as the second parameter of the callback. If no callback is specified, then the result set is returned.



## Remarks

This method can be synchronous or asynchronous. Specify a callback function to use this method asynchronously. The callback function is of the form:

```js
function(err, resultset){
                };
```



The following synchronous example shows how to use the execQuery method on a prepared statement.

```js
var iq=require('@sap/iq-client');
     var client=iq.createConnection();
     client.connect({host=XXX-XXX.iq.hdl.trial-us10.hanacloud.ondemand.com:443;uid=XXXXXXX;pwd=XXXXXXXX;enc='TLS{tls_type=rsa;direct=yes}});
     stmt=client.prepare("SELECT * FROM Customers WHERE ID >= ? AND ID < ?");
     result=stmt.execQuery([200, 300]);
     stmt.drop();
     console.log(result);
     client.disconnect();
```

