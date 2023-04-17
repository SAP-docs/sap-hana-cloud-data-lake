<!-- loio38ec278e690144219acbb0d44da23a8b -->

# close\(\[Callback\]\) Method

Closes the ResultSet object and frees up resources.



```
resultset.close([callback])
```



<a name="loio38ec278e690144219acbb0d44da23a8b__section_adq_rtx_rz"/>

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

Specifies the optional callback function.



</td>
</tr>
</table>



<a name="loio38ec278e690144219acbb0d44da23a8b__section_hw3_ckz_xrb"/>

## Remarks

This method can be synchronous or asynchronous. Specify a callback function to use this method asynchronously.

The callback function is of the following form:

```
function(err){
};
```

