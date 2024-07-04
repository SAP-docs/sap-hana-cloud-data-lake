<!-- loio81790c1c6ce21014b303ec9036456fdb -->

# sp\_list\_directory System Procedure for Data Lake Relational Engine

Returns information about the files and subdirectories in a specified directory.



<a name="loio81790c1c6ce21014b303ec9036456fdb__section_uv1_znj_g4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_list_directory( <root_path> [, <max_depth> ] )
```



<a name="loio81790c1c6ce21014b303ec9036456fdb__sp_list_directory_parameters"/>

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



<a name="loio81790c1c6ce21014b303ec9036456fdb__sp_list_directory_result_set"/>

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



<a name="loio81790c1c6ce21014b303ec9036456fdb__sp_list_directory_remarks"/>

## Remarks

These columns are useful for diagnostics:

-   *<file\_path\>*
-   *<file\_type\>*
-   *<file\_size\>*



<a name="loio81790c1c6ce21014b303ec9036456fdb__sp_list_directory_priv1"/>

## Privileges



### 

Requires all of the following:

-   EXECUTE object-level privilege on this procedure
-   EXECUTE object-level privilege on the sp\_real\_list\_directory procedure
-   READ FILE system privilege



<a name="loio81790c1c6ce21014b303ec9036456fdb__sp_list_directory_standards"/>

## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Not in the standard.



</dd>
</dl>



<a name="loio81790c1c6ce21014b303ec9036456fdb__sp_list_directory_example"/>

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


[sp_list_directory System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/3bdb623038354a3b9f12503766abe7c1.html "Returns information about the files and subdirectories in a specified directory.") :arrow_upper_right:

[sp_list_etd_files System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/0f76c8361cd84a2b8b35f74382b9265f.html "Lists the event trace data (ETD) files logged to the file container by database auditing.") :arrow_upper_right:

