<!-- loio3be890286c5f1014a6dca837390a9520 -->

# SYSEXTERNLOGIN System View for Data Lake Relational Engine

Each row in the SYSEXTERNLOGIN system view describes an external login for remote data access. The underlying system table for this view is ISYSEXTERNLOGIN.



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

user\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The user ID on the local database.



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

The remote server, as listed in the SYSSERVER system view.



</td>
</tr>
<tr>
<td valign="top">

remote\_login



</td>
<td valign="top">

VARCHAR\(128\)



</td>
<td valign="top">

The login name for the user, for the remote server.



</td>
</tr>
<tr>
<td valign="top">

remote\_password



</td>
<td valign="top">

CHAR\(3\)



</td>
<td valign="top">

Whether a password is stored. Three asterisks \(\*\*\*\) indicate that a password is stored. NULL indicates that no password is stored. You can obtain the password hash by querying the SYSEXTERNLOGINPASSWORD system view.



</td>
</tr>
</table>

Previous versions of the catalog contained a SYSEXTERNLOGINS system table. That table has been renamed to be ISYSEXTERNLOGIN \(without an 'S'\), and is the underlying table for this view.

