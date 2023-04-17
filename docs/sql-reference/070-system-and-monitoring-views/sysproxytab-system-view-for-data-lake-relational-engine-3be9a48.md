<!-- loio3be9a48b6c5f1014b2b3b9d305a13769 -->

# SYSPROXYTAB System View for Data Lake Relational Engine

Each row of the SYSPROXYTAB system view describes the remote parameters of one proxy table. The underlying system table for this view is ISYSPROXYTAB.



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

table\_object\_id



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

The object ID of the proxy table.



</td>
</tr>
<tr>
<td valign="top">

existing\_obj



</td>
<td valign="top">

CHAR\(1\)



</td>
<td valign="top">

Indicates whether the proxy table previously existed on the remote server.



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

The unique ID for the remote server associated with the proxy table.



</td>
</tr>
<tr>
<td valign="top">

remote\_location



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

The location of the proxy table on the remote server.



</td>
</tr>
<tr>
<td valign="top">

location\_escape\_char



</td>
<td valign="top">

CHAR\(1\)



</td>
<td valign="top">

The escape character that is used to escape the location delimiter.



</td>
</tr>
</table>

