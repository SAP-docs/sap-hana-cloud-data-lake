<!-- loio46cb1a874e514531a41669e3dce8a574 -->

# createParameterLobStream\(Object, Integer, Object\) Function

Creates a readable stream by using an output LOB parameter.



```
createParameterLobStream(statement, paramIndex, options)
```



<a name="loio46cb1a874e514531a41669e3dce8a574__section_adq_rtx_rz"/>

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

`statement`



</td>
<td valign="top">

Specifies a statement.



</td>
</tr>
<tr>
<td valign="top">

Integer



</td>
<td valign="top">

`paramIndex`



</td>
<td valign="top">

Specifies a zero-based parameter index.



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

Specifies properties as a JavaScript object. The only supported value is readSize. For example:

```js
{readSize: 6000}
```



</td>
</tr>
</table>

