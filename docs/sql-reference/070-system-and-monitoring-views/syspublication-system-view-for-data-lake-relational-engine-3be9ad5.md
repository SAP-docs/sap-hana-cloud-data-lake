<!-- loio3be9ad586c5f1014a798e29c04d783ac -->

# SYSPUBLICATION System View for Data Lake Relational Engine

Each row in the SYSPUBLICATION system view describes a publication. The underlying system table for this view is ISYSPUBLICATION.



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

A number uniquely identifying the publication.



</td>
</tr>
<tr>
<td valign="top">

object\_id



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

The internal ID for the publication, uniquely identifying it in the database.



</td>
</tr>
<tr>
<td valign="top">

creator



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The owner of the publication.



</td>
</tr>
<tr>
<td valign="top">

publication\_name



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

The name of the publication.



</td>
</tr>
<tr>
<td valign="top">

remarks



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

Remarks about the publication. This value is stored in the ISYSREMARK system table.



</td>
</tr>
<tr>
<td valign="top">

type



</td>
<td valign="top">

CHAR\(1\)



</td>
<td valign="top">

This column is deprecated.



</td>
</tr>
<tr>
<td valign="top">

sync\_type



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The type of synchronization for the publication. Values include:


<dl>
<dt><b>

0 \(logscan\)

</b></dt>
<dd>

This is a regular publication that uses the transaction log to upload all relevant data that has changed since the last upload.



</dd><dt><b>

1 \(scripted upload\)

</b></dt>
<dd>

For this publication, the transaction log is ignored and the upload is defined by the user using stored procedures. Information about the stored procedures is stored in the ISYSSYNCSCRIPT system table.



</dd><dt><b>

2 \(download only\)

</b></dt>
<dd>

This is a download-only publication; no data is uploaded.



</dd>
</dl>



</td>
</tr>
</table>

