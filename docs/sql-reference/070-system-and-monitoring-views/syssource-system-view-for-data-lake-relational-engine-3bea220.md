<!-- loio3bea22036c5f10148027ceb50bfb8bba -->

# SYSSOURCE System View for Data Lake Relational Engine

Each row in the SYSSOURCE system view contains the source code, if applicable, for an object listed in the SYSOBJECT system view. The underlying system table for this view is ISYSSOURCE.



> ### Restriction:  
> This data lake Relational Engine system view can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




<table>
<tr>
<th valign="top">

Column name



</th>
<th valign="top">

Data type



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

object\_id



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

The internal ID for the object whose source code is being defined.



</td>
</tr>
<tr>
<td valign="top">

source



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

This column contains the original source code for the object if the preserve\_source\_format database option is On when the object was created.



</td>
</tr>
</table>

