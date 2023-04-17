<!-- loio3be911066c5f1014bb6e8daa85182ded -->

# SYSJARCOMPONENT System View for Data Lake Relational Engine

Each row in the SYSJARCOMPONENT system view defines a JAR file component, which includes class files, manifest files, and any other JAR resource. The underlying system table for this view is ISYSJARCOMPONENT.



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

component\_id



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

The primary key containing the id of the component.



</td>
</tr>
<tr>
<td valign="top">

jar\_id



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

If the row describes a JAR, the value is the ID number of the JAR. Otherwise, the value is NULL.



</td>
</tr>
<tr>
<td valign="top">

component\_name



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

The name of the component.



</td>
</tr>
<tr>
<td valign="top">

component\_type



</td>
<td valign="top">

CHAR\(1\)



</td>
<td valign="top">

This column is no longer used and contains NULL.



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

The contents of the JAR file component. For a manifest-like component, this is character text. For a class file component, this is byte code.



</td>
</tr>
</table>

