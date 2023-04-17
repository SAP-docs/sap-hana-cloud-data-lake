<!-- loio3bf3f48e6c5f1014ad05cbe76a39d667 -->

# a\_sqlany\_bind\_param Structure

A bind parameter structure used to bind parameter and prepared statements.



```
typedef struct a_sqlany_bind_param
```



## Members

All members of a\_sqlany\_bind\_param, including inherited members.

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

public a\_sqlany\_data\_direction



</td>
<td valign="top">

direction



</td>
<td valign="top">

The direction of the data. \(input, output, input\_output\)



</td>
</tr>
<tr>
<td valign="top">

public a\_sqlany\_data\_value



</td>
<td valign="top">

value



</td>
<td valign="top">

The actual value of the data.



</td>
</tr>
<tr>
<td valign="top">

public char \*



</td>
<td valign="top">

name



</td>
<td valign="top">

Name of the bind parameter. This is only used by sqlany\_describe\_bind\_param\(\).



</td>
</tr>
</table>



## Remarks

To view examples of the a\_sqlany\_bind\_param structure in use, see any of the following sample files in the `sdk\dbcapi\examples` directory of your SQL Anywhere installation.

**Related Information**  


[sqlany\_execute\(a\_sqlany\_stmt \*\) Method](sqlany-execute-a-sqlany-stmt-method-3bf58a8.md "Executes a prepared statement.")

