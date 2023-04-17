<!-- loio11bb5d13bc71426cad2d6a42fa4e6cf4 -->

# createObjectStream\(Object\) Function

Creates a Node.js readable stream using a result set. The stream returns data as JSON objects.



```
createObjectStream(resultset)
```



<a name="loio11bb5d13bc71426cad2d6a42fa4e6cf4__section_t4n_yyr_wy"/>

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

`resultset`



</td>
<td valign="top">

The result set returned by executing a query.



</td>
</tr>
</table>



<a name="loio11bb5d13bc71426cad2d6a42fa4e6cf4__section_ggg_g1s_wy"/>

## Remarks

This method creates a Node.js stream and returns the data as JSON objects.



Create a readable object stream and fetch data from it.

```js
function fetchObjectStream() {
var conn = openConnection();
var stmt = conn.prepare('SELECT TOP 10 SCHEMA_NAME, TABLE_NAME FROM SYS.TABLES');
var rs = stmt.execQuery();
var iqStream = require('@sap/iq-client/extension/Stream');
var stream = iqStream.createObjectStream(rs);
var rows = [];
stream.on('readable', function (data) {
   var data;
   while (null !== (data = stream.read())) {
   rows.push(data);
      }
   });
   stream.on('end', function () {
      console.log(rows);
      cleanup(conn, stmt, rs);     
   });
}

```

