<!-- loio3bea339d6c5f101490739fcc01ea2b3e -->

# SYSSQLSERVERTYPE System View for Data Lake Relational Engine

The SYSSQLSERVERTYPE system view contains information relating to compatibility with Adaptive Server Enterprise. The underlying system table for this view is ISYSSQLSERVERTYPE.



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

ss\_user\_type



</td>
<td valign="top">

SMALLINT



</td>
<td valign="top">

The Adaptive Server Enterprise user type.



</td>
</tr>
<tr>
<td valign="top">

ss\_domain\_id



</td>
<td valign="top">

SMALLINT



</td>
<td valign="top">

The Adaptive Server Enterprise domain ID.



</td>
</tr>
<tr>
<td valign="top">

ss\_type\_name



</td>
<td valign="top">

VARCHAR \(30\)



</td>
<td valign="top">

The Adaptive Server Enterprise type name.



</td>
</tr>
<tr>
<td valign="top">

primary\_sa\_domain\_id



</td>
<td valign="top">

SMALLINT



</td>
<td valign="top">

The corresponding data lake Relational Engine primary domain ID.



</td>
</tr>
<tr>
<td valign="top">

primary\_sa\_user\_type



</td>
<td valign="top">

SMALLINT



</td>
<td valign="top">

The corresponding data lake Relational Engine primary user type.



</td>
</tr>
</table>

