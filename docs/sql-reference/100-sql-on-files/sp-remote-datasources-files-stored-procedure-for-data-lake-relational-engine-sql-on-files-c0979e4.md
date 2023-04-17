<!-- loioc0979e49b27f4d0d96e3a45b2fe0fe88 -->

# sp\_remote\_datasources\_files Stored Procedure for Data Lake Relational Engine \[SQL on Files\]

View a list of files that are tracked by a remote table or exist in paths referenced by datasources defined on a remote table.



> ### Restriction:  
> This topic is limited to SQL on Files use cases.
> 
> This SQL on Files stored procedure can be used when connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioc0979e49b27f4d0d96e3a45b2fe0fe88__SPDF_syntax"/>

## Syntax

```

CALL sp_remote_datasources_files(
	<remote-server-name>
	,<remote-schema-name>
	,<remote-table-name>
	[, <remote-datasource-name> ]
	[, <probe> ]
	[, <with-status> ]
)
```



<a name="loioc0979e49b27f4d0d96e3a45b2fe0fe88__SPDF_parameters"/>

## Parameters

  *<remote-server-name\>* 
 :   Use this required CHAR\(128\) parameter to specify the remote server name.

  *<remote-schema-name\>*
 :   Use this required CHAR\(128\) parameter to specify the name of the schema.

   *<remote-table-name\>* 
 :   Use this required CHAR\(128\) parameter to specify the name of the remote table.

  *<remote-datasource-name\>*
 :   Use this optional CHAR\(128\) parameter to specify the datasource name. The defaul is `null`.

  *<probe\>*
 :   Use this optional boolean flag to specify which datasource files to list.

    When *<probe\>* is set to `0`, it returns a current list of datasource files. When *<probe\>* is set to `1`, it returns a list of the latest runtime files. The default is `0`.

  *<with-status\>*
 :   Use this optional boolean flag to report more information on the file status. The default is `0`.

 

<a name="loioc0979e49b27f4d0d96e3a45b2fe0fe88__SPRD_results"/>

## Result Set


<table>
<tr>
<th valign="top">

Column Name



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

`SCHEMA_NAME`



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

Name of the schema.



</td>
</tr>
<tr>
<td valign="top">

`TABLE_NAME`



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

Name of the table.



</td>
</tr>
<tr>
<td valign="top">

`DATASOURCE_NAME`



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

Name of the datasource.



</td>
</tr>
<tr>
<td valign="top">

`DATASOURCE_IS_VALID`



</td>
<td valign="top">

BOOL



</td>
<td valign="top">

When *<probe\>* is set to `0` and *<with-status\>* is set to `0`, `DATASOURCE_IS_VALID` is `NULL`.

When *<probe\>* is set to `1`, `DATASOURCE_IS_VALID` is set to `TRUE` for all files.

If a datasource is inaccessible, `DATASOURCE_IS_VALID` is set to `FALSE`.



</td>
</tr>
<tr>
<td valign="top">

`FILE_PATH`



</td>
<td valign="top">

VARCHAR\(256\)



</td>
<td valign="top">

Internal effective path to filesystem, represented as a vflow qualified name.



</td>
</tr>
<tr>
<td valign="top">

`FILE_SIZE`



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The file size is returned as the number of bytes.



</td>
</tr>
<tr>
<td valign="top">

`FILE_ETAG`



</td>
<td valign="top">

STRING



</td>
<td valign="top">

The file identity tag unique to that file at that specific version.



</td>
</tr>
<tr>
<td valign="top">

`FILE_LAST_MODIFIED`



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

The timestamp of the last modification.



</td>
</tr>
<tr>
<td valign="top">

`FILE_STATUS`



</td>
<td valign="top">

VARCHAR\(256\)



</td>
<td valign="top">

`FILE_STATUS` is set according to the following scenarios:

 NULL
 :   The datasource is invalid.

  UNCHANGED
 :   The file belongs to both the tracked files list and runtime files list and their ETAGS are the same.

  CHANGED
 :   The file belongs to both the tracked files list and runtime files list and their ETAGS are different.

  NEW
 :   The file is present only in the runtime files list.

  DELETED
 :   The file is present only in the tracked files list.

 

</td>
</tr>
</table>



<a name="loioc0979e49b27f4d0d96e3a45b2fe0fe88__SPDF_remarks"/>

## Remarks

The specified server must be defined with the [CREATE REMOTE SERVER Statement for Data Lake Relational Engine \[SQL on Files\]](create-remote-server-statement-for-data-lake-relational-engine-sql-on-files-d9c56ec.md) to use this system procedure.



<a name="loioc0979e49b27f4d0d96e3a45b2fe0fe88__section_vrj_gjp_p4b"/>

## Privileges

You have been granted the HDL\_FILES\_SERVICE\_ADMIN role.



To get a list of files from the datasource DS1, execute the following statement:

```
CALL sp_remote_datasouces_files('SOFSRV', 'MYSCHEMA', 'MYTABLE', 'DS1', 0, 0);
```

