<!-- loio3be6c15d6c5f1014ae52e9d129434364 -->

# SYSARTICLECOL System View for Data Lake Relational Engine

Each row of the SYSARTICLECOL system view identifies a column in an article. The underlying system table for this view is ISYSARTICLECOL.



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

publication\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

A unique identifier for the publication of which the column is a part.



</td>
</tr>
<tr>
<td valign="top">

table\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The table to which the column belongs.



</td>
</tr>
<tr>
<td valign="top">

column\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The column identifier, from the SYSTABCOL system view.



</td>
</tr>
</table>

