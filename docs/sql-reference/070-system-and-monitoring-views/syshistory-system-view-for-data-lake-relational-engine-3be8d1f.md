<!-- loio3be8d1f26c5f10149c6fec07f3fa8f8e -->

# SYSHISTORY System View for Data Lake Relational Engine

Each row in the SYSHISTORY system view records a system operation on the database, such as a database start, a database calibration, and so on. The underlying system table for this view is ISYSHISTORY.



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

operation



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

The type of operation performed on the database file. The operation must be one of the following values:

INIT
:   Information about when the database was created.

UPGRADE
:   Information about when the database was upgraded.

START
:   Information about when the database was started using a specific version of the database server on a particular operating system.

LAST\_START
:   Information about the most recent time the database server was started. A LAST\_START operation is converted to a START operation when the database is started with a different version of the database server and/or on a different operating system than those values currently stored in the LAST\_START row.

DTT
:   For internal use only.

LAST\_DTT
 :   For internal use only.

LAST\_BACKUP
:   Information about the last backup, including date and time of the backup, the backup type, the files that were backed up, and the version of database server that performed the backup.



</td>
</tr>
<tr>
<td valign="top">

object\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

For any operation other than DTT and LAST\_DTT, the value in this column will be 0. For DTT and LAST\_DTT operations, this is the dbspace\_id of the dbspace as defined in the SYSDBSPACE system view.



</td>
</tr>
<tr>
<td valign="top">

sub\_operation



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

For any operation other than DTT and LAST\_DTT, the value in this column will be a set of empty single quotes \("\). For DTT and LAST\_DTT operations, this column contains the type of sub-operation performed on the dbspace. Values include:

DTT\_SET
:   The dbspace calibration has been set.

DTT\_UNSET
:   The dbspace calibration has been restored to the default setting.



</td>
</tr>
<tr>
<td valign="top">

version



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

The version and build number of the database server used to perform the operation.



</td>
</tr>
<tr>
<td valign="top">

platform



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

The operating system on which the operation was carried out.



</td>
</tr>
<tr>
<td valign="top">

first\_time



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

The local date and time the database was first started on a particular operating system with a particular version of the software.



</td>
</tr>
<tr>
<td valign="top">

last\_time



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

The most recent local date and time the database was started on a particular operating system with a particular version of the software.



</td>
</tr>
<tr>
<td valign="top">

details



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

This column stores information such as command line options used to start the database server or the capability bits enabled for the database. This information is for use by Technical Support.



</td>
</tr>
<tr>
<td valign="top">

first\_time\_utc



</td>
<td valign="top">

TIMESTAMP WITH TIME ZONE



</td>
<td valign="top">

The UTC date and time the database was first started on a particular operating system with a particular version of the software.



</td>
</tr>
<tr>
<td valign="top">

last\_time\_utc



</td>
<td valign="top">

TIMESTAMP WITH TIME ZONE



</td>
<td valign="top">

The most recent UTC date and time the database was started on a particular operating system with a particular version of the software.



</td>
</tr>
</table>

