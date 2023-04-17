<!-- loio3bea3cab6c5f1014a53cdcc2ce8af3e6 -->

# SYSSUBSCRIPTION System View for Data Lake Relational Engine

Each row in the SYSSUBSCRIPTION system view describes a subscription from one user ID \(which must have the REMOTE system privilege\) to one publication. The underlying system table for this view is ISYSSUBSCRIPTION.



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

The identifier for the publication to which the user ID is subscribed.



</td>
</tr>
<tr>
<td valign="top">

user\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The ID of the user who is subscribed to the publication.



</td>
</tr>
<tr>
<td valign="top">

subscribe\_by



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

The value of the SUBSCRIBE BY expression, if any, for the subscription.



</td>
</tr>
<tr>
<td valign="top">

created



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

The offset in the transaction log at which the subscription was created.



</td>
</tr>
<tr>
<td valign="top">

started



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

The offset in the transaction log at which the subscription was started.



</td>
</tr>
</table>

