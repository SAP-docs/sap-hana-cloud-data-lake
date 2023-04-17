<!-- loioe4b74810817e4076b6d763caa4f8ee9e -->

# setRowSetSize \(Integer\) Method

Specifies the size of the row set.



```
connection.setRowSetSize(rowSetSize)
```



<a name="loioe4b74810817e4076b6d763caa4f8ee9e__section_yzp_t45_x1b"/>

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

rowSetSize



</td>
<td valign="top">

Specifies the size of the row set. The value must be 1 \(the default\) or greater.



</td>
</tr>
</table>



<a name="loioe4b74810817e4076b6d763caa4f8ee9e__section_lzj_rwd_mgb"/>

## Remarks

This method sets the size of the row set that is fetched by Connection.execute or Statement.execute. The default row set size is 1. Increasing the row set size can improve the fetching performance.

**Related Information**  


[exec\[ute\]\(\[, Array\]\[, Object\]\[, Function\]\) Method](exec-ute-array-object-function-method-b7cae47.md "Executes the prepared SQL statement.")

[exec\[ute\]\(String\[, Array\]\[,Object\]\[, Function\]\) Method](exec-ute-string-array-object-function-method-1bec2bc.md "Executes the specified SQL statement.")

