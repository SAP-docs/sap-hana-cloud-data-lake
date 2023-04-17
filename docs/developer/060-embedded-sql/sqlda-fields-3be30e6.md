<!-- loio3be30e636c5f10149f689438c533e70c -->

# SQLDA Fields

The SQLDA \(SQL Descriptor Area\) is a data structure consisting of a number of fields.



The SQLDA fields have the following meanings:


<table>
<tr>
<th valign="top">

Field



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 *sqldaid* 



</td>
<td valign="top">

An 8-byte character field that contains the string SQLDA as an identification of the SQLDA structure. This field helps in debugging when you are looking at memory contents.



</td>
</tr>
<tr>
<td valign="top">

 *sqldabc* 



</td>
<td valign="top">

A 32-bit integer containing the length of the SQLDA structure.



</td>
</tr>
<tr>
<td valign="top">

 *sqln* 



</td>
<td valign="top">

The number of variable descriptors allocated in the sqlvar array.



</td>
</tr>
<tr>
<td valign="top">

 *sqld* 



</td>
<td valign="top">

The number of variable descriptors that are valid \(contain information describing a host variable\). This field is set by the DESCRIBE statement. As well, you can set it when supplying data to the database server.



</td>
</tr>
<tr>
<td valign="top">

 *sqlvar* 



</td>
<td valign="top">

An array of descriptors of type struct sqlvar, each describing a host variable.



</td>
</tr>
</table>

