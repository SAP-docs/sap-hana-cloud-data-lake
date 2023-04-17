<!-- loioef7dcb31a04d409a9725493358a41070 -->

# ResultSet Class

Represents a result set.



```
class ResultSet
```



## Members

All members of ResultSet.

 **Methods** 


<table>
<tr>
<th valign="top">

Method



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 [close\(\[Callback\]\) Method](close-callback-method-38ec278.md)



</td>
<td valign="top">

Closes the ResultSet object and frees up resources.



</td>
</tr>
<tr>
<td valign="top">

 [getColumnCount\(\) Method](getcolumncount-method-0572527.md)



</td>
<td valign="top">

Gets the number of columns in the current result set.



</td>
</tr>
<tr>
<td valign="top">

[getColumnInfo\(\) Method](getcolumninfo-method-a2c2c87.md)



</td>
<td valign="top">

Gets specified column information.



</td>
</tr>
<tr>
<td valign="top">

[getColumnName\(Integer\) Method](getcolumnname-integer-method-c4674b2.md)



</td>
<td valign="top">

Gets the name of the column for the specified zero-based column index.



</td>
</tr>
<tr>
<td valign="top">

[getData\(Integer, Integer, Buffer, Integer, Integer\[, Function\]\) Method](getdata-integer-integer-buffer-integer-integer-function-method-5953c59.md) 



</td>
<td valign="top">

Reads a stream of bytes from the specified LOB column, starting at the location indicated by dataOffset, into the buffer, starting at the location indicated by bufferOffset.



</td>
</tr>
<tr>
<td valign="top">

[getRowCount\(\) Method](getrowcount-method-5cd5328.md)



</td>
<td valign="top">

Gets the number of rows in the current result set.



</td>
</tr>
<tr>
<td valign="top">

[getValue\(Integer\) Method](getvalue-integer-method-6ddbf64.md) 



</td>
<td valign="top">

Gets the value of the specified column.



</td>
</tr>
<tr>
<td valign="top">

[getValueLength\(Integer\) Method](getvaluelength-integer-method-8908642.md)



</td>
<td valign="top">

Gets the length of a LOB column or a character string type.



</td>
</tr>
<tr>
<td valign="top">

[getValues\(\[Options\]\[, Callback\]\) Method](getvalues-options-callback-method-74fb958.md) 



</td>
<td valign="top">

Gets an object with the column names and values of the current row.



</td>
</tr>
<tr>
<td valign="top">

[isClosed\(\) Method](isclosed-method-1bf45fb.md)



</td>
<td valign="top">

Checks if the result set is closed.



</td>
</tr>
<tr>
<td valign="top">

[isNull\(Integer\) Method](isnull-integer-method-46d4970.md)



</td>
<td valign="top">

Checks if the specified column is NULL.



</td>
</tr>
<tr>
<td valign="top">

 [next\(\[Function\]\) Method](next-function-method-c345ce5.md)



</td>
<td valign="top">

Gets the next row in the result set.



</td>
</tr>
<tr>
<td valign="top">

[nextResult\(\[Function\]\) Method](nextresult-function-method-8c757a0.md) 



</td>
<td valign="top">

Gets the next result set.



</td>
</tr>
</table>

