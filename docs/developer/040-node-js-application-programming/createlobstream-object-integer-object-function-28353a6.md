<!-- loio28353a644a444f2bb5f80df7b1a37f8e -->

# createLobStream \(Object, Integer, Object\) Function

Creates a Node.js readable stream by using a result set. The stream fetches data as LOB columns.



```
createLobStream(resultset, columnIndex, options)
```



<a name="loio28353a644a444f2bb5f80df7b1a37f8e__section_adq_rtx_rz"/>

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

A result set.



</td>
</tr>
<tr>
<td valign="top">

Integer



</td>
<td valign="top">

`columnIndex`



</td>
<td valign="top">

The index of the LOB column.



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

Properties that are specified as a JavaScript object. The only supported value is readSize. For example:

```js
{readSize: 6000}
```



</td>
</tr>
</table>



<a name="loio28353a644a444f2bb5f80df7b1a37f8e__section_g1q_xtx_rz"/>

## Remarks

This function creates a Node.js readable stream by using a result set. The stream fetches data as LOB columns.



The following example shows the total bytes fetched for the LOB.

```js
'use strict';

var async = require('async');
var iq = require('@sap/iq-client');
var iqStream = require('@sap/iq-client/extension/Stream');

var connOptions = {
    serverNode: 'myserver:443',
    uid: 'DBA',
    pwd: 'sql'
};

var conn = iq.createConnection();
conn.connect(connOptions);

console.log('Create test table ......');
conn.exec('create table TEST_LOBS(ID integer primary key, DATA long binary)');

console.log('Insert rows ......');
var stmt = conn.prepare('insert into TEST_LOBS values(?, ?)');
var buffer = null;
var ids = [1, 2, 3, 4, 5];
for (var i = 0; i < ids.length; i++) {
    buffer = new Buffer(new Array(1024 * 64 + ids[i]).join('ab'), "ascii");
    stmt.exec([ids[i], buffer]);
}

console.log('Fetching rows ......');
async.eachOfLimit(ids, ids.length, function (id, i, cb) {
    var stmt = conn.prepare('select ID, DATA from TEST_LOBS where ID = ?');
    var rs = stmt.execQuery([id]);
    rs.next(function (err, ret) {
        if (err) {
            console.log(err);
        } else {
            var id = rs.getValue(0);
            var lob = [];
            var totalBytes = 0;
            var lobStream = iqStream.createLobStream(rs, 1,
               { readSize: 6000 });

            lobStream.on('data', function (buffer) {
                if (buffer) {
                    totalBytes += buffer.length;
                }
            });
            lobStream.on('end', function () {
                console.log(id + ', total bytes --- ' + totalBytes);
            });
            lobStream.on('error', function (error) {
                console.log(error);
            });
        }
    });
});
```

