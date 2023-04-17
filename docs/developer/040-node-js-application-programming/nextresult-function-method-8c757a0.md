<!-- loio8c757a028c5b433fbb88774082d1aeb9 -->

# nextResult\(\[Function\]\) Method

Moves to the next result set.



```
resultset.nextResult([callback])
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

Returns true if there are more result sets and false otherwise.



## Remarks

This method checks to see if there are more result sets and moves to the next available result set.

The callback function is of the following form:

```
function(err, result){
};
```

