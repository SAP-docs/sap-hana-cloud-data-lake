<!-- loio3bf3d2506c5f1014827fd629c4260767 -->

# a\_sqlany\_bind\_param\_info Structure

Gets information about the currently bound parameters.



```
typedef struct a_sqlany_bind_param_info
```



## Members

All members of a\_sqlany\_bind\_param\_info, including inherited members.

 **Variables** 


<table>
<tr>
<th valign="top">

Modifier and Type



</th>
<th valign="top">

Variable



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

public char \*



</td>
<td valign="top">

name



</td>
<td valign="top">

A pointer to the name of the parameter.



</td>
</tr>
<tr>
<td valign="top">

public a\_sqlany\_data\_direction



</td>
<td valign="top">

direction



</td>
<td valign="top">

The direction of the parameter.



</td>
</tr>
<tr>
<td valign="top">

public a\_sqlany\_data\_value



</td>
<td valign="top">

input\_value



</td>
<td valign="top">

Information about the bound input value.



</td>
</tr>
<tr>
<td valign="top">

public a\_sqlany\_data\_value



</td>
<td valign="top">

output\_value



</td>
<td valign="top">

Information about the bound output value.



</td>
</tr>
<tr>
<td valign="top">

public a\_sqlany\_native\_type



</td>
<td valign="top">

native\_type



</td>
<td valign="top">

The native type of the column in the database.



</td>
</tr>
<tr>
<td valign="top">

public unsigned short



</td>
<td valign="top">

precision



</td>
<td valign="top">

The precision.



</td>
</tr>
<tr>
<td valign="top">

public unsigned short



</td>
<td valign="top">

scale



</td>
<td valign="top">

The scale.



</td>
</tr>
<tr>
<td valign="top">

public size\_t



</td>
<td valign="top">

max\_size



</td>
<td valign="top">

The maximum size a data value in this column can take.



</td>
</tr>
</table>



## Remarks

sqlany\_get\_bind\_param\_info\(\) can be used to populate this structure.

To view examples of the a\_sqlany\_bind\_param\_info structure in use, see any of the following sample files in the `sdk\dbcapi\examples` directory of your SQL Anywhere installation.

**Related Information**  


[sqlany\_execute\(a\_sqlany\_stmt \*\) Method](sqlany-execute-a-sqlany-stmt-method-3bf58a8.md "Executes a prepared statement.")

