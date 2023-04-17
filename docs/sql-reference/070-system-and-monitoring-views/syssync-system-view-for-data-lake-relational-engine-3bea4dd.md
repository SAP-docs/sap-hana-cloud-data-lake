<!-- loio3bea4dd76c5f1014b9938f9b6fbaf40f -->

# SYSSYNC System View for Data Lake Relational Engine

The SYSSYNC system view contains information relating to synchronization.



> ### Restriction:  
> This data lake Relational Engine system view can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



The "option" and server\_connect columns of the underlying table, ISYSSYNC, contain sensitive information such as passwords. You must have the SELECT ANY TABLE and ACCESS USER PASSWORD system privileges to select from this view. The SYSSYNC2 consolidated view provides public access to the same data without the sensitive data.

The underlying system table for this view is ISYSSYNC.


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

sync\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

A number that uniquely identifies the row.



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

This value is always D.



</td>
</tr>
<tr>
<td valign="top">

publication\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

A publication\_id found in the SYSPUBLICATION system view.



</td>
</tr>
<tr>
<td valign="top">

progress



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

The log offset of the last successful upload.



</td>
</tr>
<tr>
<td valign="top">

site\_name



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

A user name.



</td>
</tr>
<tr>
<td valign="top">

"option"



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

Synchronization options.



</td>
</tr>
<tr>
<td valign="top">

server\_connect



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

The address or URL of the server.



</td>
</tr>
<tr>
<td valign="top">

server\_conn\_type



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

The communication protocol, such as TCP/IP, to use when synchronizing.



</td>
</tr>
<tr>
<td valign="top">

last\_download\_time



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Indicates the last time a download stream was received from the server.



</td>
</tr>
<tr>
<td valign="top">

last\_upload\_time



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Indicates the last time \(measured at the server\) that information was successfully uploaded. The default is jan-1-1900.



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

The log offset at which the subscription was created.



</td>
</tr>
<tr>
<td valign="top">

log\_sent



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

The log progress up to which information has been uploaded. It is not necessary that an acknowledgment of the upload be received for the entry in this column to be updated.



</td>
</tr>
<tr>
<td valign="top">

generation\_number



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

For file-base downloads, the last generation number received for this subscription. The default is 0.



</td>
</tr>
<tr>
<td valign="top">

extended\_state



</td>
<td valign="top">

VARCHAR\(1024\)



</td>
<td valign="top">

For internal use only.



</td>
</tr>
<tr>
<td valign="top">

script\_version



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

Indicates the script version used by the CREATE and ALTER SYNCHRONIZATION SUBSCRIPTION statements and the START SYNCHRONIZATION SCHEMA CHANGE statement.



</td>
</tr>
<tr>
<td valign="top">

subscription\_name



</td>
<td valign="top">

CHAR \(128\)



</td>
<td valign="top">

The name of the subscription.



</td>
</tr>
<tr>
<td valign="top">

server\_protocol



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

For internal use only. Contains a value used internally to identify the version of the synchronization server.



</td>
</tr>
</table>

