<!-- loio3be9319a6c5f1014923186f27403a030 -->

# SYSLOGINPOLICYOPTION System View for Data Lake Relational Engine

The underlying system table for this view is ISYSLOGINPOLICYOPTION.



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

login\_policy\_id



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

A unique identifier for the login policy.



</td>
</tr>
<tr>
<td valign="top">

login\_option\_name



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

The name of the login policy.



</td>
</tr>
<tr>
<td valign="top">

login\_option\_value



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

The value of the login policy at the time it was created.



</td>
</tr>
</table>
