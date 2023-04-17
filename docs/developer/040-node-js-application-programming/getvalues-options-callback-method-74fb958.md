<!-- loio74fb958f447649fabf91de61311d8433 -->

# getValues\(\[Options\]\[, Callback\]\) Method

Gets an object with the column names and values of the current row.



```
resultset.getValues([options] [, callback])
```



<a name="loio74fb958f447649fabf91de61311d8433__section_rxd_r3y_xnb"/>

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

 `options` 



</td>
<td valign="top">

Specifies the optional object containing the options for defining the representation of rows in the result.



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



## Returns

If the options parameter is specified as “\{asArray: true\}”, this method returns an array consisting of all column values for the current row. Otherwise, it returns an object that consists of a set of column names and value pairs for the current row.

If no callback is specified, then the result is returned.



<a name="loio74fb958f447649fabf91de61311d8433__section_fxd_z3j_zrb"/>

## Remarks

This method can be synchronous or asynchronous. Specify a callback function to use this method asynchronously.

The callback function is of the following form:

```
function(err, result){
};
```

