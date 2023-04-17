<!-- loiobd73153df8364d689924dc8ef93d59aa -->

# createStatement\(Object, String\[, Function\]\) Function

Creates a statement object which executes a SQL statement with readable streams for input LOB parameters.



```
createStatement(connection, sql[, callback])
```



<a name="loiobd73153df8364d689924dc8ef93d59aa__section_adq_rtx_rz"/>

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

Object



</td>
<td valign="top">

 `connection` 



</td>
<td valign="top">

Specifies the connection object.



</td>
</tr>
<tr>
<td valign="top">

String



</td>
<td valign="top">

 `sql` 



</td>
<td valign="top">

Specifies the SQL statement.



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



<a name="loiobd73153df8364d689924dc8ef93d59aa__section_g1q_xtx_rz"/>

## Remarks

The created object has two functions:


<table>
<tr>
<th valign="top">

Function



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

```js
exec: function (params, callback)
```



</td>
<td valign="top">

Executes the SQL statement.

`params` specifies an optional array of binding parameters. You can add readable streams to `params`.



</td>
</tr>
<tr>
<td valign="top">

```js
drop: function (callback)
```



</td>
<td valign="top">

Drops the statement.



</td>
</tr>
</table>



The following example creates a statement object:

```js
var Readable = require('stream').Readable;

var stream1 = new Readable();
stream1.push('blob1234');
stream1.push('blob5678');
stream1.push(null);
var stream2 = new Readable();
stream2.push('clob1234');
stream2.push('clob5678');
stream2.push(null);

var conn = openConnection();

conn.exec('CREATE TABLE HDL_NODE_TEST(ID INT, C_BLOB LONG BINARY, C_CLOB LONG VARCHAR)');
conn.setAutoCommit(false);

var sql = 'INSERT INTO HDL_NODE_TEST(ID, C_BLOB, C_CLOB) VALUES(?, ?, ?)';
iqStream.createStatement(conn, sql, function (err, stmt) {
   if (err) {
     console.log(err);
   } else {
     stmt.exec([1, stream1, stream2], function (err, result) {
       if (err) {
         console.log(err);
       } else {
         console.log(result);
       }
     stmt.drop(function (err) {
         if (err) {
            console.log(err);
         }
         conn.close();
       });
    });
   }
  });
```

