<!-- loio9154c85a905a4710977219a772216fd9 -->

# sendParameterData\(paramIndex, buffer\[, callback\]\) Method

Sends LOB data to the server in chunks.



```
Statement.sendParameterData(paramIndex, buffer[, callback])
```



<a name="loio9154c85a905a4710977219a772216fd9__section_ljv_2kc_5z"/>

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

Integer



</td>
<td valign="top">

`paramIndex`



</td>
<td valign="top">

Specifies the index of the LOB parameter.



</td>
</tr>
<tr>
<td valign="top">

Buffer



</td>
<td valign="top">

`buffer`



</td>
<td valign="top">

Specifies the data in the buffer is sent to the server.



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



<a name="loio9154c85a905a4710977219a772216fd9__section_zxd_gkc_5z"/>

## Returns

Returns a Boolean value that indicates whether the method succeeded.



<a name="loio9154c85a905a4710977219a772216fd9__section_k1f_ypc_5z"/>

## Remarks

Call `sendParameterData` to append the LOB data to the statement and then call the `execute` method to specify the `sendParameterData` to TRUE for each LOB parameter.



The following example shows how to call the execute method before using sendParameterData:

```js
var conn = openConnection();

var buffer = new Buffer(5000);
for (var i = 0; i < buffer.length; i++) {
    buffer[i] = 97;
}

var id = 1;
conn.setAutoCommit(false);
var stmt = conn.prepare('INSERT INTO TEST_TABLE(ID, C_BLOB, C_CLOB) VALUES(?, ?, ?)');
stmt.sendParameterData(1, buffer);
stmt.sendParameterData(1, buffer);
stmt.sendParameterData(1, null);
stmt.sendParameterData(2, buffer);
stmt.sendParameterData(2, buffer);
stmt.sendParameterData(2, buffer);
stmt.sendParameterData(2, null);
stmt.exec([id, { sendParameterData: true }, { sendParameterData: true }]);
conn.commit();
```

**Related Information**  


[exec\[ute\]\(\[, Array\]\[, Object\]\[, Function\]\) Method](exec-ute-array-object-function-method-b7cae47.md "Executes the prepared SQL statement.")

