<!-- loio3bea70906c5f1014901efbe57e06183f -->

# SYSSYNCSCRIPT System View for Data Lake Relational Engine

Each row in the SYSSYNCSCRIPT system view identifies a stored procedure for scripted upload. This view is almost identical to the SYSSYNCSCRIPTS view, except that the values in this view are in their raw format.



> ### Restriction:  
> This data lake Relational Engine system view can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



The underlying system table for this view is ISYSSYNCSCRIPT.


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

pub\_object\_id



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

The object ID of the publication to which the script belongs.



</td>
</tr>
<tr>
<td valign="top">

table\_object\_id



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

The object ID of the table to which the script applies.



</td>
</tr>
<tr>
<td valign="top">

type



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The type of upload procedure.



</td>
</tr>
<tr>
<td valign="top">

proc\_object\_id



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

The object ID of the stored procedure to use for the publication.



</td>
</tr>
</table>

