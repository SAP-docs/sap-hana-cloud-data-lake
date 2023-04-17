<!-- loioe432e094300e479198a415a432bb8667 -->

# Connection Class

Represents the connection to the database.



```
class Connection
```



## Members

All members of the connection.

 **Methods** 


<table>
<tr>
<th valign="top">

Type



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

 



</td>
<td valign="top">

[abort\(\[Function\]\) Method](abort-function-method-3a42289.md)



</td>
<td valign="top">

Aborts the running database request that is being executed on the connection.



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

[clearPool\(\[Function\]\) Method](clearpool-function-method-08917a9.md)



</td>
<td valign="top">

Empties the connection pool.



</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

 [commit\(\[Function\]\) Method](commit-function-method-968d7eb.md)



</td>
<td valign="top">

Performs a commit on the connection.



</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

[connect\(\{String | Object\}\[, Function\]\) Method](connect-string-object-function-method-13e47ad.md) 



</td>
<td valign="top">

Creates a new connection to the database by using a connection string or a hash of connection parameters that is passed in as a parameter.



</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

[\{disconnect | close | end\}\(\[Function\]\) Method](disconnect-close-end-function-method-8dee077.md) 



</td>
<td valign="top">

Closes the current connection.



</td>
</tr>
<tr>
<td valign="top">

Result, Number, or Undefined.



</td>
<td valign="top">

 [exec\[ute\]\(String\[, Array\]\[,Object\]\[, Function\]\) Method](exec-ute-string-array-object-function-method-1bec2bc.md)



</td>
<td valign="top">

Executes the specified SQL statement.



</td>
</tr>
<tr>
<td valign="top">

Statement



</td>
<td valign="top">

 [prepare\(String\[, Function\]\) Method](prepare-string-function-method-d26edca.md)



</td>
<td valign="top">

Prepares the specified SQL statement and returns a Statement object.



</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

[rollback\(\[Function\]\) Method](rollback-function-method-c3adaa4.md) 



</td>
<td valign="top">

Performs a rollback on the connection.



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

[setAutoCommit\(Boolean\) Method](setautocommit-boolean-method-233cdbb.md) 



</td>
<td valign="top">

Changes the autocommit setting for the connection.



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

[setRowSetSize \(Integer\) Method](setrowsetsize-integer-method-e4b7481.md)



</td>
<td valign="top">

Specifies the size of the row set.



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

[state\(\) Method](state-method-7ba9675.md)



</td>
<td valign="top">

Returns a string that indicates the state of the connection.



</td>
</tr>
</table>



<a name="loioe432e094300e479198a415a432bb8667__section_orh_53b_2gb"/>

## Remarks

Once the connection is made, if there are network issues, any call using the connection fails and returns an error.



The following example uses synchronous calls to create a new connection to data lake Relational Engine, issue a SQL query against the server, display the result set, and then disconnect from the server.

```js
var iq=require('@sap/iq-client');
var client=iq.createConnection();
client.connect(host=XXX-XXX.iq.hdl.trial-us10.hanacloud.ondemand.com:443;uid=XXXXXXX;pwd=XXXXXXXX;enc='TLS{tls_type=rsa;direct=yes});
console.log('Connected');
result = client.exec("SELECT * FROM Customers");
console.log(result);
client.disconnect();
console.log('Disconnected');
```

The following example performs the same tasks as the previous example by using callbacks to perform asynchronous calls. Error checking is included.

```js
var iq = require('@sap/iq-client');
var client = iq.createConnection();
client.connect("host=XXX-XXX.iq.hdl.trial-us10.hanacloud.ondemand.com:443;uid=XXXXXXX;pwd=XXXXXXXX;enc='TLS{tls_type=rsa;direct=yes}",
  function(err)
  {
    if(err) {
      console.error("Connect error: ",err);
    } else {
      console.log("Connected");
                
      client.exec("SELECT * FROM Customers",
        function(err,rows)
        {
          if(err) {
            console.error("Error: ",err);
          } else {
            console.log(rows);
          }
        }
      );
        
      client.disconnect(
        function(err)
        {
          if(err) {
            console.error("Disconnect error: ", err);
          } else {
            console.log("Disconnected");
          }
        }
      );
    }
  }
);
```

The following example also uses callbacks, but the functions are not inlined.

```js
var iq=require('@sap/iq-client');
var client=iq.createConnection();
client.connect("host=XXX-XXX.iq.hdl.trial-us10.hanacloud.ondemand.com:443;uid=XXXXXXX;pwd=XXXXXXXX;enc='TLS{tls_type=rsa;direct=yes}", async_connect);

function async_connect(err)
{  
  if(err) {
    console.error("Connect error: ", err);
  } else {
    console.log("Connected");

    client.exec("SELECT FROM Customers",async_results);

  }
}

function async_results(err,rows)
{
  if(err) {
    console.error("Error: ", err);
  } else {
    console.log(rows);
  }

  client.disconnect(async_disconnect);
}

function async_disconnect(err)
{
  if(err) {
    console.error("Disconnect error: ", err);
  } else {
    console.log("Disconnected");
  }
}

```

You can also pass connection parameters into the createConnection function. Those connection parameters are combined with connection parameters in the connect\(\) function call to get the connection string used for the connection. Use a hash of connection parameters or a connection string fragment in either call.

