<!-- loioc345ce5da47848d3a102a20e98bed3f0 -->

# next\(\[Function\]\) Method

Gets the next row in the result set.



```
resultset.next([callback])
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

Returns true if there are more rows in the result set and false otherwise.



## Remarks

This method attempts to fetch the next row of the result set, returning `true` when successful and `false` if there are no more rows.

This method can be synchronous or asynchronous. Specify a callback function to use this method asynchronously.

The callback function is of the following form:

```
function(err, result){
};
```

