<!-- loio3be880736c5f1014879efbc3f85d9194 -->

# SYSEXTERNENV System View for Data Lake Relational Engine

Each row in the SYSEXTERNENV system view describes the information needed to identify and launch each of the external environments. The underlying system table for this view is ISYSEXTERNENV.



<a name="loio3be880736c5f1014879efbc3f85d9194__section_v1w_qbq_b4b"/>

## Usage

This data lake Relational Engine system view can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




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

A unique identifier for the external environment.

</td>
</tr>
<tr>
<td valign="top">

name

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

This column identifies the name of the external environment or language. It is one of *java*, *perl*, *php*, and so on.

</td>
</tr>
<tr>
<td valign="top">

scope

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

This column is either C for CONNECTION or D for DATABASE respectively. The scope column identifies if the external environment is launched as one-per-connection or one-per-database.

For one-per-connection external environments \(like PERL, PHP, JS, C\_ESQL32, C\_ESQL64, C\_ODBC32, and C\_ODBC64\), there is one instance of the external environment for each connection using the external environment. For a one-per-connection, the external environment terminates when the connection terminates.

For one-per-database external environments \(such as JAVA\), there is one instance of the external environment for each database using the external environment. The one-per-database external environment terminates when the database is stopped.

</td>
</tr>
<tr>
<td valign="top">

support\_result\_sets

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

This column identifies those external environments that can return result sets. All external environments can return result sets except PERL, PHP, and JS.

</td>
</tr>
<tr>
<td valign="top">

location

</td>
<td valign="top">

LONG VARCHAR

</td>
<td valign="top">

This column identifies the location on the database server computer where the executable/binary for the external environment can be found. It includes the executable/binary name. This path can either be fully qualified or relative. If the path is relative, then the executable/binary must be in a location where the database server can find it.

</td>
</tr>
<tr>
<td valign="top">

options

</td>
<td valign="top">

LONG VARCHAR

</td>
<td valign="top">

This column identifies any options required on the command line to launch the executable associated with the external environment. Do not modify this column.

</td>
</tr>
<tr>
<td valign="top">

user\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

When the external environment is initially launched, it must make a connection back to the database to set things up for the external environment's usage. By default, this connection is made using the HDLADMIN user ID, but if the database administrator prefers to have the external environment use a different user ID with MANAGE ANY EXTERNAL OBJECT system privilege, then the user\_id column would indicate that different user ID instead. Typically, this column is NULL and the database server, by default, uses the HDLADMIN user ID.

</td>
</tr>
</table>

