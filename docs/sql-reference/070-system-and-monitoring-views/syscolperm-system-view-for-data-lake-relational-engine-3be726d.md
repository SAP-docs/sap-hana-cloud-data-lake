<!-- loio3be726d16c5f1014a99fa1418cc708d9 -->

# SYSCOLPERM System View for Data Lake Relational Engine

The GRANT statement can give UPDATE, SELECT, or REFERENCES privileges to individual columns in a table. Each column with UPDATE, SELECT, or REFERENCES privileges is recorded in one row of the SYSCOLPERM system view. The underlying system table for this view is ISYSCOLPERM.



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

table\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The table number for the table containing the column.



</td>
</tr>
<tr>
<td valign="top">

grantee



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The ID of the user that has been given the privilege on the column. If the user ID is the PUBLIC role, then all users have the privilege on the column.



</td>
</tr>
<tr>
<td valign="top">

grantor



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The ID of the user that granted the privilege.



</td>
</tr>
<tr>
<td valign="top">

column\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

This column number, together with the table\_id, identifies the column for which privilege has been granted.



</td>
</tr>
<tr>
<td valign="top">

privilege\_type



</td>
<td valign="top">

SMALLINT



</td>
<td valign="top">

The number in this column indicates the kind of column privilege \(16=REFERENCES, 1=SELECT, or 8=UPDATE\).



</td>
</tr>
<tr>
<td valign="top">

is\_grantable



</td>
<td valign="top">

CHAR\(1\)



</td>
<td valign="top">

Indicates if the privilege on the column was granted WITH GRANT OPTION.



</td>
</tr>
</table>

