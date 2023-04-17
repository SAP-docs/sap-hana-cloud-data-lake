<!-- loio3393cbb307d24ae3bb25aa58246cfc54 -->

# Statement Class

Represents a prepared statement.



```
class Statement
```



## Members

All members of Statement.

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

[drop\(\[Function\]\) Method](drop-function-method-c59f09e.md) 



</td>
<td valign="top">

Drops the prepared SQL statement.



</td>
</tr>
<tr>
<td valign="top">

 [exec\[ute\]\(\[, Array\]\[, Object\]\[, Function\]\) Method](exec-ute-array-object-function-method-b7cae47.md) 



</td>
<td valign="top">

Executes the prepared SQL statement.



</td>
</tr>
<tr>
<td valign="top">

[exec\[ute\]Batch\(Array\[, Function\]\) Method](exec-ute-batch-array-function-method-909ddba.md)



</td>
<td valign="top">

Submits the command for batch execution and if the command executes successfully, then this method returns the number of rows affected.



</td>
</tr>
<tr>
<td valign="top">

[exec\[ute\]Query\(\[Array\]\[, Function\]\) Method](exec-ute-query-array-function-method-c3f672c.md)



</td>
<td valign="top">

Executes the prepared SQL statement and returns a result set object.



</td>
</tr>
<tr>
<td valign="top">

[functionCode\(\) Method](functioncode-method-f011ed7.md)



</td>
<td valign="top">

Gets the function code of the statement.



</td>
</tr>
<tr>
<td valign="top">

[getColumnInfo\(\) Method](getcolumninfo-method-63a3d66.md)



</td>
<td valign="top">

Gets specified column information.



</td>
</tr>
<tr>
<td valign="top">

[getData\(Integer, Integer, Buffer, Integer, Integer\[, Function\]\) Method](getdata-integer-integer-buffer-integer-integer-function-method-54ecc6f.md)



</td>
<td valign="top">

Reads a stream of bytes from the specified output LOB parameter.



</td>
</tr>
<tr>
<td valign="top">

[getParameterInfo\(\) Method](getparameterinfo-method-c5e9658.md)



</td>
<td valign="top">

Gets the specified parameter information.



</td>
</tr>
<tr>
<td valign="top">

[getParameterValue\(Integer\[, Function\]\) Method](getparametervalue-integer-function-method-d8a0ac6.md)



</td>
<td valign="top">

Retrieves output parameter values.



</td>
</tr>
<tr>
<td valign="top">

[getPrintLines\(\) Method](getprintlines-method-3905c2a.md)



</td>
<td valign="top">

Allows applications to access to messages printed from a stored procedure via SQLSCRIPT\_PRINT:PRINT\_LINE.



</td>
</tr>
<tr>
<td valign="top">

[isValid\(\) Method](isvalid-method-7932805.md)



</td>
<td valign="top">

Checks whether the statement is valid.



</td>
</tr>
<tr>
<td valign="top">

[sendParameterData\(paramIndex, buffer\[, callback\]\) Method](sendparameterdata-paramindex-buffer-callback-method-9154c85.md)



</td>
<td valign="top">

Sends LOB data to the server in chunks.



</td>
</tr>
<tr>
<td valign="top">

[setTimeout\(Integer\) Method](settimeout-integer-method-472c240.md)



</td>
<td valign="top">

Changes the default timeout for a statement.



</td>
</tr>
</table>



## Remarks

The Statement object is for SQL statements that are executed multiple times.

