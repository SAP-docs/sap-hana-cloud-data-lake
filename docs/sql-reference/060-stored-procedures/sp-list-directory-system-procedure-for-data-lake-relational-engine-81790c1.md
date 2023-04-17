<!-- loio81790c1c6ce21014b303ec9036456fdb -->

# sp\_list\_directory System Procedure for Data Lake Relational Engine

Returns information about the files and subdirectories in a specified directory.



```
sp_list_directory(
<root_path>
[, <max_depth> ]
)
```



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE_EXECUTE Usage Examples for Running Procedures](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/3e7f86d36c3c4335822e2908ee320623.html "The process to run a procedure depends on if the procedure returns a results set.") :arrow_upper_right: for more information.



<a name="loio81790c1c6ce21014b303ec9036456fdb__sp_list_directory_parameters"/>

## Parameters

  *<root\_path\>* 
 :   Use this LONG NVARCHAR parameter to specify the directory path.

    For diagnostic files, *<root\_path\>* requires the common prefix:

    -   `/diag/logs/` for diagnostic logs

    -   `/diag/audit/` for auditing \(ETD\) files


   *<max\_depth\>* 
 :   Use this optional INTEGER parameter to specify the maximum number of directories to traverse. A max\_depth of NULL, 0, or a negative value results in all subdirectories of *<root\_path\>* being traversed. The default is NULL.

 

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



<a name="loio81790c1c6ce21014b303ec9036456fdb__sp_list_directory_privileges"/>

## Privileges

You need to have EXECUTE privilege on the system procedure, as well as the READ FILE system privilege.



<a name="loio81790c1c6ce21014b303ec9036456fdb__sp_list_directory_standards"/>

## Standards

 ANSI/ISO SQL Standard
 :   Not in the standard.

 

Example result:


<table>
<tr>
<th valign="top">

file\_path



</th>
<th valign="top">

file\_type



</th>
<th valign="top">

file\_size



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



</td>
<td valign="top">

saptu



</td>
<td valign="top">

1970-01-01 00:00:00.000-05:00



</td>
<td valign="top">

2021-11-25 01:33:13.000-05:00



</td>
<td valign="top">

1970-01-01 00:00:00.000-05:00



</td>
<td valign="top">

drwxr-xr-x



</td>
</tr>
<tr>
<td valign="top">

/diag/logs/mpx-coord-0/iqaas\_20211125\_000000.002\_mpx-coord-0.iqmsg



</td>
<td valign="top">

F



</td>
<td valign="top">

632846



</td>
<td valign="top">

saptu



</td>
<td valign="top">

1970-01-01 00:00:00.000-05:00



</td>
<td valign="top">

2021-11-25 01:30:06.000-05:00



</td>
<td valign="top">

1970-01-01 00:00:00.000-05:00



</td>
<td valign="top">

\-rwxr-xr-x



</td>
</tr>
<tr>
<td valign="top">

/diag/logs/mpx-coord-0/iqaas\_20211124\_174654.405\_mpx-coord-0.iqmsg



</td>
<td valign="top">

F



</td>
<td valign="top">

6683



</td>
<td valign="top">

saptu



</td>
<td valign="top">

1970-01-01 00:00:00.000-05:00



</td>
<td valign="top">

2021-11-24 17:47:08.000-05:00



</td>
<td valign="top">

1970-01-01 00:00:00.000-05:00



</td>
<td valign="top">

\-rwxr-xr-x



</td>
</tr>
<tr>
<td valign="top">

/diag/logs/mpx-coord-0/iqaas\_20211124\_174421.990\_mpx-coord-0.iqmsg



</td>
<td valign="top">

F



</td>
<td valign="top">

22277



</td>
<td valign="top">

saptu



</td>
<td valign="top">

1970-01-01 00:00:00.000-05:00



</td>
<td valign="top">

2021-11-24 17:46:51.000-05:00



</td>
<td valign="top">

1970-01-01 00:00:00.000-05:00



</td>
<td valign="top">

\-rwxr-xr-x



</td>
</tr>
<tr>
<td valign="top">

/diag/logs/mpx-coord-0/iqaas\_20211124\_174029.462\_mpx-coord-0.iqmsg



</td>
<td valign="top">

F



</td>
<td valign="top">

4072



</td>
<td valign="top">

saptu



</td>
<td valign="top">

1970-01-01 00:00:00.000-05:00



</td>
<td valign="top">

2021-11-24 17:40:37.000-05:00



</td>
<td valign="top">

1970-01-01 00:00:00.000-05:00



</td>
<td valign="top">

\-rwxr-xr-x



</td>
</tr>
</table>

**Related Information**  


[sp_list_directory System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/3bdb623038354a3b9f12503766abe7c1.html "Returns information about the files and subdirectories in a specified directory.") :arrow_upper_right:

[sp_list_etd_files System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/0f76c8361cd84a2b8b35f74382b9265f.html "Lists the event trace data (ETD) files logged to the file container by database auditing.") :arrow_upper_right:

