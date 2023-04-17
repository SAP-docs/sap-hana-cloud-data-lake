<!-- loioc38fa5765a7b484c813e728b534019ee -->

# sp\_remote\_datasources Stored Procedure for Data Lake Relational Engine \[SQL on Files\]

View a list of all the datasources on a remote table using a system procedure.



> ### Restriction:  
> This topic is limited to SQL on Files use cases.
> 
> This SQL on Files stored procedure can be used when connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioc38fa5765a7b484c813e728b534019ee__SPRD_syntax"/>

## Syntax

```
sp_remote_datasources(
	<remote-server-name>
	[,	<remote-schema-name>
	[,	<remote-table-name>	] ]
)
```



<a name="loioc38fa5765a7b484c813e728b534019ee__SPRD_parameters"/>

## Parameters

  *<remote-server-name\>* 
 :   *<remote-server-name\>* must be specified. Use this CHAR\(128\) parameter to specify the remote server name.

  *<remote-schema-name\>*
 :   The name of the schema.

   *<remote-table-name\>* 
 :   Use this optional CHAR\(128\) parameter to specify the name of the remote table. The default is '%'. *<remote-table-name\>* can be specified as null to match any remote table.

 

<a name="loioc38fa5765a7b484c813e728b534019ee__SPRD_results"/>

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

VARCHAR\(256\) or CHAR\(128\)



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

VARCHAR\(256\) or CHAR\(128\)



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

VARCHAR\(256\) or CHAR\(128\)



</td>
<td valign="top">

Name of the datasource.



</td>
</tr>
<tr>
<td valign="top">

`DATASOURCE_OPTIONS`



</td>
<td valign="top">

STRING



</td>
<td valign="top">

JSON string of all the options.



</td>
</tr>
<tr>
<td valign="top">

`DATASOURCE_COLUMNS`



</td>
<td valign="top">

STRING



</td>
<td valign="top">

JSON string of all the columns and their options.



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

`FILE_FORMAT`



</td>
<td valign="top">

ENUM



</td>
<td valign="top">

CSV, PARQUET, ORC



</td>
</tr>
<tr>
<td valign="top">

`FILE_SYSTEM`



</td>
<td valign="top">

ENUM



</td>
<td valign="top">

S3, ...



</td>
</tr>
<tr>
<td valign="top">

`DATASOURCE_ENCODING`



</td>
<td valign="top">

ENUM



</td>
<td valign="top">

UTF\_8, CESU\_8, ISO\_8859\_1



</td>
</tr>
<tr>
<td valign="top">

`ZIPPED`



</td>
<td valign="top">

BOOL



</td>
<td valign="top">

 



</td>
</tr>
</table>



<a name="loioc38fa5765a7b484c813e728b534019ee__SPRD_remarks"/>

## Remarks

The specified server must be defined with the [CREATE REMOTE SERVER Statement for Data Lake Relational Engine \[SQL on Files\]](create-remote-server-statement-for-data-lake-relational-engine-sql-on-files-d9c56ec.md) to use this system procedure.



<a name="loioc38fa5765a7b484c813e728b534019ee__section_vrj_gjp_p4b"/>

## Privileges

You have been granted the HDL\_FILES\_SERVICE\_ADMIN role.



The following example returns information about the datasources providing data to `ExternalTable1` at the server `RemoteSOF`:

```
CALL sp_remote_datasources( 'RemoteSOF', 'ExternalTable1' );
```

