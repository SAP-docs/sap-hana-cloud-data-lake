<!-- loio3bdb623038354a3b9f12503766abe7c1 -->

# sp\_list\_directory System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns information about the files and subdirectories in a specified directory.



<a name="loio3bdb623038354a3b9f12503766abe7c1__section_gz5_gcf_pzb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:

-   Connected to SAP HANA database as a SAP HANA database user and using SAP HANA database REMOTE\_EXECUTE\_QUERY.
-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_list_directory( <root_path> [, <max_depth> ] )
```



## Parameters


<dl>
<dt><b>

*<root\_path\>* 

</b></dt>
<dd>

Use this LONG NVARCHAR parameter to specify the directory path.

For diagnostic files, *<root\_path\>* requires the common prefix:

-   `/diag/logs/` for diagnostic logs

-   `/diag/audit/` for auditing \(ETD\) files




</dd><dt><b>

*<max\_depth\>* 

</b></dt>
<dd>

Use this optional INTEGER parameter to specify the maximum number of directories to traverse. A max\_depth of NULL, 0, or a negative value results in all subdirectories of *<root\_path\>* being traversed. The default is NULL.



</dd>
</dl>



## Result Set


<table>
<tr>
<th valign="top">

Column name

</th>
<th valign="top">

Column description

</th>
</tr>
<tr>
<td valign="top">

*<file\_path\>*

</td>
<td valign="top">

LONG NVARCHAR - The path to a file or subdirectory within the specified directory. If *<directory\_path\>* is specified as a relative path, then the returned *<file\_path\>* is a relative value. Otherwise, *<file\_path\>* is an absolute value. When the sandbox feature is enabled, the absolute and relative paths refer to the directory where the main database file is located.

</td>
</tr>
<tr>
<td valign="top">

*<file\_type\>*

</td>
<td valign="top">

NVARCHAR\(1\) - F if the *<file\_path\>* value is a file or D when the *<file\_path\>* value is a directory.

</td>
</tr>
<tr>
<td valign="top">

*<file\_size\>* 

</td>
<td valign="top">

UNSIGNED BIGINT - Specifies the size in bytes of the file or NULL when *<file\_path\>* value is a directory

</td>
</tr>
<tr>
<td valign="top">

*<owner\>*

</td>
<td valign="top">

NVARCHAR\(128\) - The owner of the file or directory.

</td>
</tr>
<tr>
<td valign="top">

*<create\_date\_time\>*

</td>
<td valign="top">

TIMESTAMP WITH TIME ZONE - The date and time the file or directory was created, returned in the database server's time zone.

</td>
</tr>
<tr>
<td valign="top">

*<modified\_date\_time\>*

</td>
<td valign="top">

TIMESTAMP WITH TIME ZONE - The date and time the file or directory was last modified, returned in the database server's time zone.

</td>
</tr>
<tr>
<td valign="top">

*<access\_date\_time\>*

</td>
<td valign="top">

TIMESTAMP WITH TIME ZONE - The date and time the file or directory was last accessed, returned in the database server's time zone.

</td>
</tr>
<tr>
<td valign="top">

*<permissions\>*

</td>
<td valign="top">

VARCHAR\(10\) - The set of access permissions for the file or directory.

</td>
</tr>
</table>



## Remarks

These columns are useful for diagnostics:

-   *<file\_path\>*
-   *<file\_type\>*
-   *<file\_size\>*



<a name="loio3bdb623038354a3b9f12503766abe7c1__section_jzh_12b_1yb"/>

## Privileges



### 

The privileges required depend on your data lake Relational Engine \(SAP HANA DB-Managed\) connection method:


<dl>
<dt><b>

Connected to SAP HANA database as a SAP HANA database user and using REMOTE\_EXECUTE\_QUERY:

</b></dt>
<dd>

Requires the REMOTE EXECUTE privilege on the remote source *<hana\_relational\_container\_schema\>*\_SOURCE.

-   See [REMOTE\_EXECUTE\_QUERY Guidance and Examples for Running Stored Procedures](remote-execute-query-guidance-and-examples-for-running-stored-procedures-3e7f86d.md).




</dd><dt><b>

Connected directly to data lake Relational Engine as a data lake Relational Engine user:

</b></dt>
<dd>

Requires all of the following:

-   EXECUTE object-level privilege on this procedure
-   EXECUTE object-level privilege on the sp\_real\_list\_directory procedure
-   READ FILE system privilege



</dd>
</dl>



## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Not in the standard.



</dd>
</dl>



## Examples

This example returns the files and subdirectories for diagnostic logs, one level down.

```
CALL sp_list_directory( '/diag/logs','1');
```


<table>
<tr>
<th valign="top">

file\_path

</th>
<th valign="top">

file\_

type

</th>
<th valign="top">

file\_

size

</th>
<th valign="top">

owner

</th>
<th valign="top">

create\_date\_time

</th>
<th valign="top">

modified\_date\_time

</th>
<th valign="top">

access\_date\_time

</th>
<th valign="top">

permissions

</th>
</tr>
<tr>
<td valign="top">

/diag/logs/mpx-coord-0

</td>
<td valign="top">

D

</td>
<td valign="top">

NULL

</td>
<td valign="top">

122181570

</td>
<td valign="top">

1970-01-01 00:00:00.000-00:00

</td>
<td valign="top">

2023-09-28 13:35:33.000-00:00

</td>
<td valign="top">

1970-01-01 00:00:00.000-00:00

</td>
<td valign="top">

drwxr-x---

</td>
</tr>
<tr>
<td valign="top">

/diag/logs/mpx-coord-0

</td>
<td valign="top">

FD

</td>
<td valign="top">

NULL

</td>
<td valign="top">

122181570

</td>
<td valign="top">

1970-01-01 00:00:00.000-00:00

</td>
<td valign="top">

2023-09-28 13:35:33.000-00:00

</td>
<td valign="top">

1970-01-01 00:00:00.000-00:00

</td>
<td valign="top">

drwxr-x---

</td>
</tr>
</table>

**Related Information**  


[sp_list_directory System Procedure for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/81790c1c6ce21014b303ec9036456fdb.html "Returns information about the files and subdirectories in a specified directory.") :arrow_upper_right:

