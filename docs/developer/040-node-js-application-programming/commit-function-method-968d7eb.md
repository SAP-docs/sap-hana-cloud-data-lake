<!-- loio968d7eb8b5bf4673b426551e40d3b065 -->

# commit\(\[Function\]\) Method

Performs a commit on the connection.



```
connection.commit([callback])
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

This method performs a commit on the connection if autoCommit is set to false. By default, inserts, updates, and deletes are committed when statements are executed.

This method can be synchronous or asynchronous. Specify a callback function to use this method asynchronously. The callback function is of the form:

```js
function(err){
    };
```



The following example shows how to use the commit method synchronously.

```js
var iq=require('@sap/iq-client');
    var client=iq.createConnection();
    client.connect("host=XXX-XXX.iq.hdl.trial-us10.hanacloud.ondemand.com:443;uid=XXXXXXX;pwd=XXXXXXXX;enc='TLS{tls_type=rsa;direct=yes}");
    client.setAutoCommit(false);
    stmt=client.prepare(
    "INSERT INTO Departments "
    + "(DepartmentID,DepartmentName, DepartmentHeadID)"
    + "VALUES(?,?,?)");
    var result=stmt.exec([600, 'Eastern Sales', 902]);
    result+=stmt.exec([700, 'Western Sales', 902]);
    stmt.drop();
    console.log("Number of rows added: " + result);
    result=client.exec("SELECT * FROM Departments");
    console.log(result);
    client.commit();
    client.disconnect();
```

