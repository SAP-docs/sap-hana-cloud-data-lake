<!-- loio9cc8e366e5434419987145e76966f042 -->

# createArrayStream\(Object\) Function

Creates a node.js readable stream by using a result set.



```
createArrayStream(resultset)
```



<a name="loio9cc8e366e5434419987145e76966f042__section_t4n_yyr_wy"/>

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



<a name="loio9cc8e366e5434419987145e76966f042__section_id4_mb2_sz"/>

## Returns

The stream returns data as JavaScript arrays.



<a name="loio9cc8e366e5434419987145e76966f042__section_ggg_g1s_wy"/>

## Remarks

This method creates a node.js stream and returns the data as JavaScript arrays.



Create a readable array stream and fetch data from it.

```js
function fetchArrayStream() {
        var conn = openConnection();
        var stmt = conn.prepare('SELECT TOP 10 SCHEMA_NAME, TABLE_NAME FROM SYS.TABLES');
        var rs = stmt.execQuery();
        var iqStream = require('@sap/iq-client/extension/Stream.js');
        var stream = iqStream.createArrayStream(rs);
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

