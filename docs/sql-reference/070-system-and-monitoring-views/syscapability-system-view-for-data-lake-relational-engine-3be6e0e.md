<!-- loio3be6e0ed6c5f1014aa52d6cc4bbb136a -->

# SYSCAPABILITY System View for Data Lake Relational Engine

Each row of the SYSCAPABILITY system view specifies the status of a capability on a remote database server. The underlying system table for this view is ISYSCAPABILITY.



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

capid



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

The ID of the capability, as listed in the SYSCAPABILITYNAME system view.



</td>
</tr>
<tr>
<td valign="top">

srvid



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The server to which the capability applies, as listed in the SYSSERVER system view.



</td>
</tr>
<tr>
<td valign="top">

capvalue



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

The value of the capability.



</td>
</tr>
</table>

