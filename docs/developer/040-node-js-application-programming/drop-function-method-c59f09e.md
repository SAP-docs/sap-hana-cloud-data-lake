<!-- loioc59f09efe7c14972b81cd5f7e3ebde6d -->

# drop\(\[Function\]\) Method

Drops the prepared SQL statement.



```
statement.drop ([callback])
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

This method drops the prepared statement and frees up resources.

This method can be either synchronous or asynchronous depending on whether or not a callback function is specified. The callback function is of the form:

```js
function(err)
    {
    };
```



The following synchronous example shows how to use the drop method on a prepared statement.

```js
var iq=require('@sap/iq-client');
    var client=iq.createConnection();
    client.connect({host=XXX-XXX.iq.hdl.trial-us10.hanacloud.ondemand.com:443;uid=XXXXXXX;pwd=XXXXXXXX;enc='TLS{tls_type=rsa;direct=yes}});
    stmt=client.prepare("SELECT * FROM Customers WHERE ID >= ? AND ID < ?");
    result=stmt.exec([200, 300]);
    stmt.drop();
    console.log(result);
    client.disconnect();
```

