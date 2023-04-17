<!-- loio3be7c5646c5f10148118dd6c4d3c5001 -->

# SYSDBFILE System View for Data Lake Relational Engine

Each row in the SYSDBFILE system view describes a dbspace file. The underlying system table for this view is ISYSDBFILE.



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

dbfile\_id



</td>
<td valign="top">

SMALLINT



</td>
<td valign="top">

For internal use only.



</td>
</tr>
<tr>
<td valign="top">

dbspace\_id



</td>
<td valign="top">

SMALLINT



</td>
<td valign="top">

Each dbspace file in a database is assigned a unique number. The system dbspace contains all system objects and has a dbspace\_id of 0.



</td>
</tr>
<tr>
<td valign="top">

dbfile\_name



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

A unique name for the dbspace. It is used in the CREATE TABLE command.



</td>
</tr>
<tr>
<td valign="top">

file\_name



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

The file name for the dbspace.



</td>
</tr>
<tr>
<td valign="top">

lob\_map



</td>
<td valign="top">

LONG VARBIT



</td>
<td valign="top">

For internal use only.



</td>
</tr>
</table>

