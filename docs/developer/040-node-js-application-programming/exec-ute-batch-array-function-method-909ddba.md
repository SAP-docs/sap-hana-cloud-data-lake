<!-- loio909ddba0bce54ec6b0d6c8c750a59b51 -->

# exec\[ute\]Batch\(Array\[, Function\]\) Method

Submits the command for batch execution and if the command executes successfully, then this method returns the number of rows affected.



```
statement.exec[ute]Batch ([params][, callback])
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

An array of bind parameters to execute.



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

If you do not specify a callback function, then the number of rows affected is returned.



## Remarks

This method can be synchronous or asynchronous. Specify a callback function to use this method asynchronously. The callback function is of the form:

```js
function(err, ret){
   };
```



The following synchronous example shows how to use the exec method on a prepared statement.

```js
var iq=require('@sap/iq-client');
   var client=iq.createConnection();
   client.connect({host=XXX-XXX.iq.hdl.trial-us10.hanacloud.ondemand.com:443;uid=XXXXXXX;pwd=XXXXXXXX;enc='TLS{tls_type=rsa;direct=yes}});
   stmt=client.prepare("INSERT INTO Customers(ID, NAME) VALUES(?, ?)");
   result=stmt.execBatch([[1, 'Company 1'], [2, 'Company 2']]);
   stmt.drop();
   console.log(result);
   client.disconnect();
```

