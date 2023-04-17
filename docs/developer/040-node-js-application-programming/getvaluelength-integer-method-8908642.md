<!-- loio890864210e554c24b663f5b73f5c535c -->

# getValueLength\(Integer\) Method

Gets the length of a LOB column or a character string type.



```
resultset.getValueLength(colIndex)
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

Integer



</td>
<td valign="top">

`colIndex`



</td>
<td valign="top">

The zero-based column index.



</td>
</tr>
</table>



## Returns

Returns the length of a LOB or character string type, or -1 if that information is not available. If the column is a NULL value, then 0 is returned.

