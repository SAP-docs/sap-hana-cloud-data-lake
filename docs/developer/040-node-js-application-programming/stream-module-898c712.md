<!-- loio898c71278e074a1b8075e644cfd9e4ea -->

# Stream Module

A Node.js module that exposes streaming functions.



```
var stream = require('@sap/iq-client/extension/StreamIQ.js');
```



<a name="loio898c71278e074a1b8075e644cfd9e4ea__section_p2t_frd_wy"/>

## Members

All functions exposed in the stream module.

 **Functions** 


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

[createArrayStream\(Object\) Function](createarraystream-object-function-9cc8e36.md)



</td>
<td valign="top">

Creates a Node.js readable stream by using a result set. The stream returns data as JavaScript arrays.



</td>
</tr>
<tr>
<td valign="top">

[createLobStream \(Object, Integer, Object\) Function](createlobstream-object-integer-object-function-28353a6.md)



</td>
<td valign="top">

Creates a Node.js readable stream by using a result set. The stream fetches data as LOB columns.



</td>
</tr>
<tr>
<td valign="top">

[createObjectStream\(Object\) Function](createobjectstream-object-function-11bb5d1.md)



</td>
<td valign="top">

Creates a Node.js readable stream using a result set. The stream returns data as JSON objects.



</td>
</tr>
<tr>
<td valign="top">

[createParameterLobStream\(Object, Integer, Object\) Function](createparameterlobstream-object-integer-object-function-46cb1a8.md)



</td>
<td valign="top">

Creates a readable stream by using an output LOB parameter.



</td>
</tr>
<tr>
<td valign="top">

[createStatement\(Object, String\[, Function\]\) Function](createstatement-object-string-function-function-bd73153.md)



</td>
<td valign="top">

Creates a statement object which executes a SQL statement with readable streams for input LOB parameters.



</td>
</tr>
</table>

