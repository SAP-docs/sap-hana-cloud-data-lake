<!-- loio3be7dd276c5f10149869e22c1a67a29e -->

# SYSDBSPACE System View for Data Lake Relational Engine

Each row in the SYSDBSPACE system view describes a dbspace file. The underlying system table for this view is ISYSDBSPACE.



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

dbspace\_id



</td>
<td valign="top">

SMALLINT



</td>
<td valign="top">

Unique number identifying the dbspace. The system dbspace contains all system objects and has a dbspace\_id of 0.



</td>
</tr>
<tr>
<td valign="top">

object\_id



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

The object ID of the dbspace.



</td>
</tr>
<tr>
<td valign="top">

dbspace\_name



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

store\_type



</td>
<td valign="top">

TINYINT



</td>
<td valign="top">

For internal use only.



</td>
</tr>
<tr>
<td valign="top">

saved\_cache\_pages



</td>
<td valign="top">

LONG VARBIT



</td>
<td valign="top">

For internal use only.



</td>
</tr>
</table>



<a name="loio3be7dd276c5f10149869e22c1a67a29e__section_e1j_whp_k5b"/>

## Additional Information

Users require the SELECT object-level privilege granted on the system view to see information.

