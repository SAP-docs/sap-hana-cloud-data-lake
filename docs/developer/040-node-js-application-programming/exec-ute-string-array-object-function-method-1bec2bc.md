<!-- loio1bec2bc5259d4e9da54a2e1908f246ee -->

# exec\[ute\]\(String\[, Array\]\[,Object\]\[, Function\]\) Method

Executes the specified SQL statement.



```
connection.exec[ute](sql[, params] [, options] [, callback])
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

Specifies the SQL statement to execute.



</td>
</tr>
<tr>
<td valign="top">

Array



</td>
<td valign="top">

`params`



</td>
<td valign="top">

Specifies an optional array of bind parameters.



</td>
</tr>
<tr>
<td valign="top">

Object



</td>
<td valign="top">

`options`



</td>
<td valign="top">

Specifies the optional object containing the options for defining the representation of rows in the result.



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

Returns the number of rows affected and undefined.

If no callback is specified, then the result is returned.



## Remarks

This method takes in an SQL statement and an optional array of bind parameters to execute.

This method can be synchronous or asynchronous. Specify a callback function to use this method asynchronously. The callback function is of the form:

```js
function(err, result)
    {
    };
```

For queries that produce result sets, the result set object is returned as the second parameter of the callback function. For INSERT, UPDATE, and DELETE statements, the number of rows affected is returned as the second parameter of the callback. For other statements, the result is undefined.



The following synchronous example shows how to use the exec method.

```js
var iq=require('@sap/iq-client');
    var client=iq.createConnection();
    client.connect("host=XXX-XXX.iq.hdl.trial-us10.hanacloud.ondemand.com:443;uid=XXXXXXX;pwd=XXXXXXXX;enc='TLS{tls_type=rsa;direct=yes}");
    result=client.exec("SELECT * FROM Customers");
    console.log(result);
    client.disconnect();
```

The following synchronous example shows how to specify bind parameters.

```js
var iq=require('@sap/iq-client');
    var client=iq.createConnection();
    client.connect("host=XXX-XXX.iq.hdl.trial-us10.hanacloud.ondemand.com:443;uid=XXXXXXX;pwd=XXXXXXXX;enc='TLS{tls_type=rsa;direct=yes}");
    result=client.exec(
    "SELECT * FROM Customers WHERE ID >=? AND ID <?",
    [300, 400]);
    console.log(result);
    client.disconnect();
```

To return a separate object per row for each table when you specify a SQL statement as a join with overlapping column names, set the `nestTables` option to TRUE. For example:

```js
var command = 'SELECT top 1 * FROM t1 JOIN t2 on t1.id = t2.id';
    var options = {
      nestTables: true
    };
    connection.exec(command, options, function(err, rows) {
    /
```

Specifying the above example returns an array like the following example:

```js
[{
  T1: {
   ID: 1,
   A: 't1.1.a',
   B: 't1.1.b'
  },
  T2: {
   ID: 1
   A: 't2.1.a',
   B: 't2.1.b'
  }
}]
```

To return all rows as an array where the order of the column values is exactly the same as in Statement.getColumnInfo, set the `rowsAsArray` option to TRUE. For example:

```js
var command = 'SELECT top 1 * FROM t1 JOIN t2 on t1.id = t2.id';
    var options = {
      rowsAsArray: true
    };
    client.exec(command, options, function(err, rows) {
    / 
```

Specifying the above example returns an array like the following example:

```js
[[
  1,
  't1.1.a',
  't1.1.b',
  1,
  't2.1.a',
  't2.1.b'
]]
```

