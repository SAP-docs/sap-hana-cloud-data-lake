<!-- loio3a42289776804033b0eaf5ba7c1be0db -->

# abort\(\[Function\]\) Method

Aborts the running database request that is being executed on the connection.



```
connection.abort([callback] )
```



<a name="loio3a42289776804033b0eaf5ba7c1be0db__section_dv1_hjq_4cb"/>

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



<a name="loio3a42289776804033b0eaf5ba7c1be0db__section_nlx_y4j_zrb"/>

## Remarks

This method does nothing if there is no running request on the connection. If there is a running request on the connection, the client aborts waiting for the reply and then drops the connection to the server. Future method calls on the aborted and dropped connection may result in the connection being reconnected.

