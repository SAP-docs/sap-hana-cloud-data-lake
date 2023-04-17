<!-- loio3be9ee026c5f10148aac94297d73d3d1 -->

# SYSREMOTETYPE System View for Data Lake Relational Engine

The SYSREMOTETYPE system view contains information about remote tables. The underlying system table for this view is ISYSREMOTETYPE.



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

type\_id



</td>
<td valign="top">

SMALLINT



</td>
<td valign="top">

Identifies which of the message systems is to be used to send messages to the user.



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

The internal ID for the remote type, uniquely identifying it in the database.



</td>
</tr>
<tr>
<td valign="top">

type\_name



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

The name of the message system.



</td>
</tr>
<tr>
<td valign="top">

publisher\_address



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

The address of the remote database publisher.



</td>
</tr>
<tr>
<td valign="top">

remarks



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

Remarks about the remote type. This value is stored in the ISYSREMARK system table.



</td>
</tr>
</table>

