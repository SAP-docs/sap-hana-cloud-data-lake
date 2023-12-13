<!-- loioe9fdd659ccd646848bdf02d401046679 -->

# sp\_remote\_schemas Stored Procedure for Data Lake Relational Engine \[SQL on Files\]

View a list of all the schemas on a remote server using a system procedure.



<a name="loioe9fdd659ccd646848bdf02d401046679__section_fry_b3b_nqb"/>

## Usage

-   This topic is limited to SQL on Files use cases.
-   This SQL on Files stored procedure can be used when connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioe9fdd659ccd646848bdf02d401046679__SPRS_syntax"/>

## Syntax

```
sp_remote_schemas(
	<remote-server-name>, 
	[	<remote-schema-name>	]
);
```



<a name="loioe9fdd659ccd646848bdf02d401046679__SPRS_parameters"/>

## Parameters


<dl>
<dt><b>

*<remote-server-name\>* 

</b></dt>
<dd>

Use this CHAR\(128\) parameter to specify the remote server name. *<remote-server-name\>* must be specified.



</dd><dt><b>

*<remote-schema-name\>*

</b></dt>
<dd>

The name of the schema.



</dd>
</dl>



<a name="loioe9fdd659ccd646848bdf02d401046679__SPRS_results"/>

## Result Set

A table named RemoteSchemas with a single column titled SCHEMA\_NAME.

-   If *<remote-schema-name\>* is provided the table returns at most one row.

-   If *<remote-schema-name\>* is not provided the table returns all the schemas defined for SQL on Files.




<a name="loioe9fdd659ccd646848bdf02d401046679__SPRS_remarks"/>

## Remarks

The specified server must be defined with the [CREATE REMOTE SERVER Statement for Data Lake Relational Engine \[SQL on Files\]](create-remote-server-statement-for-data-lake-relational-engine-sql-on-files-d9c56ec.md) to use this system procedure.



<a name="loioe9fdd659ccd646848bdf02d401046679__section_w4c_gt2_j4b"/>

## Privileges

You have been granted the HDL\_FILES\_SERVICE\_ADMIN role.



## Example

The following example returns the schemas on the remote server `sof`:

```
CALL sp_remote_schemas ( 'sof' ) ;
```

The following example returns the schema name for the remote server `sof` and the schema `sof_schema`:

```
CALL sp_remote_schemas ( 'sof', 'sof_schema' ) ;
```

