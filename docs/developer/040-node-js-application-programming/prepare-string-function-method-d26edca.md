<!-- loiod26edca6e7b84ba9b4cfbecb3518289a -->

# prepare\(String\[, Function\]\) Method

Prepares the specified SQL statement and returns a Statement object.



```
connection.prepare(sql[, callback])
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

String



</td>
<td valign="top">

`sql`



</td>
<td valign="top">

The SQL statement to be prepared.



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



## Returns

If no callback is specified, then a Statement object is returned.



## Remarks

This method can be synchronous or asynchronous. Specify a callback function to use this method asynchronously. The callback function is of the form:

```js
function(err, Statement)
    {
    };
```



The following synchronous example shows how to use the prepare method.

```js
var iq=require('@sap/iq-client');
    var client=iq.createConnection();
    client.connect("host=XXX-XXX.iq.hdl.trial-us10.hanacloud.ondemand.com:443;uid=XXXXXXX;pwd=XXXXXXXX;enc='TLS{tls_type=rsa;direct=yes}");
    stmt=client.prepare("SELECT * FROM Customers WHERE ID >= ? AND ID < ?");
    var result=stmt.exec([200, 300]);
    console.log(result);
    client.disconnect();
```

