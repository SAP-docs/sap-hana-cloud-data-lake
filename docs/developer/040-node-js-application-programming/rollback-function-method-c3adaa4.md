<!-- loioc3adaa40322841118002a3c2c86aa619 -->

# rollback\(\[Function\]\) Method

Performs a rollback on the connection.



```
connection.rollback([callback])
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

This method can be synchronous or asynchronous. Specify a callback function to use this method asynchronously. The callback function is of the form:

```js
function(err){
    };
```



The following synchronous example shows how to use the rollback method.

```js
var iq=require('@sap/iq-client');
    var client=iq.createConnection();
    client.setAutoCommit(false);
    client.connect("host=XXX-XXX.iq.hdl.trial-us10.hanacloud.ondemand.com:443;uid=XXXXXXX;pwd=XXXXXXXX;enc='TLS{tls_type=rsa;direct=yes}");
    stmt=client.prepare(
    "INSERT INTO Departments"
    +"(DepartmentID, DepartmentName, DepartmentHeadID)"
    +"VALUES(?,?,?)");
    var result=stmt.exec([600, 'Eastern Sales',902]);
    result+=stmt.exec([700, 'Western Sales', 902]);
    stmt.drop();
    console.log("Number of rows added: " + result);
    result=client.exec("SELECT * FROM Departments");
    console.log(result);
    client.rollback();
    client.disconnect();
```

