<!-- loio3be888176c5f101493a8b6b21381355a -->

# SYSEXTERNENVOBJECT System View for Data Lake Relational Engine

Each row in the SYSEXTERNENVOBJECT system view describes an installed external object. The underlying system table for this view is ISYSEXTERNENVOBJECT.



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

A unique identifier for the external object.



</td>
</tr>
<tr>
<td valign="top">

extenv\_id



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

The unique identifier for the external environment \(SYSEXTERNENV.object\_id\).



</td>
</tr>
<tr>
<td valign="top">

owner



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

This column identifies the creator/owner of the external object.



</td>
</tr>
<tr>
<td valign="top">

name



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

This column identifies the name of the external object as specified in the INSTALL EXTERNAL OBJECT statement.



</td>
</tr>
<tr>
<td valign="top">

contents



</td>
<td valign="top">

LONG BINARY



</td>
<td valign="top">

The contents of the external object.



</td>
</tr>
<tr>
<td valign="top">

update\_time



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

This column identifies the last local time the object was modified \(or installed\).



</td>
</tr>
<tr>
<td valign="top">

update\_time\_utc



</td>
<td valign="top">

TIMESTAMP WITH TIME ZONE



</td>
<td valign="top">

This column identifies the last UTC time the object was modified \(or installed\).



</td>
</tr>
</table>

