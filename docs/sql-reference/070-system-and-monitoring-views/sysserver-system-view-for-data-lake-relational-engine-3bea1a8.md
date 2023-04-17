<!-- loio3bea1a826c5f1014a08c927368ee86e5 -->

# SYSSERVER System View for Data Lake Relational Engine

Each row in the SYSSERVER system view describes a remote server. The underlying system table for this view is ISYSSERVER.



> ### Restriction:  
> This data lake Relational Engine system view can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



> ### Note:  
> Previous versions of the catalog contained a SYSSERVERS system table. That table has been renamed to be ISYSSERVER \(without an 'S'\), and is the underlying table for this view.


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

srvid



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

An identifier for the remote server.



</td>
</tr>
<tr>
<td valign="top">

srvname



</td>
<td valign="top">

VARCHAR\(128\)



</td>
<td valign="top">

The name of the remote server.



</td>
</tr>
<tr>
<td valign="top">

srvclass



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

The server class, as specified in the CREATE SERVER statement.



</td>
</tr>
<tr>
<td valign="top">

srvinfo



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

Server information.



</td>
</tr>
<tr>
<td valign="top">

srvreadonly



</td>
<td valign="top">

CHAR\(1\)



</td>
<td valign="top">

Whether the server is read-only.



</td>
</tr>
</table>

