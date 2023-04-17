<!-- loio5953c59b06a3434da77b7411351a744c -->

# getData\(Integer, Integer, Buffer, Integer, Integer\[, Function\]\) Method

Reads a stream of bytes from the specified output LOB parameter.



```
statement.getData(paramIndex, dataOffset, buffer, bufferOffset, length[, callback])
```



<a name="loio5953c59b06a3434da77b7411351a744c__section_jdb_2p5_z1b"/>

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

Specifies the zero-based parameter index.



</td>
</tr>
<tr>
<td valign="top">

Integer



</td>
<td valign="top">

`dataOffset`



</td>
<td valign="top">

Specifies the index within the column where the read operation begins, in bytes.

For string columns, the index is in bytes based on the column encoding.

For CHAR, VARCHAR and LONG VARCHAR, the byte index is in the database character set.

For NCHAR, NVARCHAR and LONG NVARCHAR, the byte index is in the UTF-8 Unicode encoding.



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

Specifies the buffer into which to copy the data.



</td>
</tr>
<tr>
<td valign="top">

Integer



</td>
<td valign="top">

`bufferOffset`



</td>
<td valign="top">

Specifies the index within the buffer to which the data is copied, in bytes.



</td>
</tr>
<tr>
<td valign="top">

Integer



</td>
<td valign="top">

`length`



</td>
<td valign="top">

Specifies the maximum number of bytes to read.



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



<a name="loio5953c59b06a3434da77b7411351a744c__section_kdb_2p5_z1b"/>

## Returns

Returns the actual number of bytes read.



<a name="loio5953c59b06a3434da77b7411351a744c__section_ldb_2p5_z1b"/>

## Remarks

This method supports asynchronous callbacks.

For string columns, the data filled into the buffer is in the UTF-8 encoding. If all the column data doesn't fit in the buffer, the end of the buffer may contain a partial UTF-8 character.

