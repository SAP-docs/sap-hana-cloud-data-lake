<!-- loio3be9496b6c5f101497cee97c4f7404f5 -->

# SYSOBJECT System View for Data Lake Relational Engine

Each row in the SYSOBJECT system view describes a database object. The underlying system table for this view is ISYSOBJECT.



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

The internal ID for the object, uniquely identifying it in the database.



</td>
</tr>
<tr>
<td valign="top">

status



</td>
<td valign="top">

TINYINT



</td>
<td valign="top">

The status of the object. Values include:


<dl>
<dt><b>

1 \(valid\)

</b></dt>
<dd>

The object is available for use by the database server. This status is synonymous with ENABLED. That is, if you ENABLE an object, the status changes to VALID.



</dd><dt><b>

2 \(invalid\)

</b></dt>
<dd>

An attempt to recompile the object after an internal operation has failed, for example, after a schema-altering modification to an object on which it depends. The database server continues to try to recompile the object whenever it is referenced in a statement.



</dd><dt><b>

4 \(disabled\)

</b></dt>
<dd>

The object has been explicitly disabled by the user, for example using an ALTER TABLE...DISABLE VIEW DEPENDENCIES statement.



</dd>
</dl>



</td>
</tr>
<tr>
<td valign="top">

object\_type



</td>
<td valign="top">

TINYINT



</td>
<td valign="top">

Type of object.



</td>
</tr>
<tr>
<td valign="top">

creation\_time



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

The local date and time when the object was created.



</td>
</tr>
<tr>
<td valign="top">

object\_type\_str



</td>
<td valign="top">

CHAR \(128\)



</td>
<td valign="top">

Type of object.



</td>
</tr>
<tr>
<td valign="top">

creation\_time\_utc



</td>
<td valign="top">

TIMESTAMP WITH TIME ZONE



</td>
<td valign="top">

The UTC date and time when the object was created.



</td>
</tr>
</table>

