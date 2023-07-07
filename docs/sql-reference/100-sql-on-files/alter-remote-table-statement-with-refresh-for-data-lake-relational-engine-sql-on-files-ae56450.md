<!-- loioae5645003caf4d14bcd05ca4d8f3219e -->

# ALTER \(Remote\) TABLE Statement with REFRESH for Data Lake Relational Engine \[SQL on Files\]

Alter the refresh mode of a table.



> ### Restriction:  
> This topic is limited to SQL on Files use cases.
> 
> This SQL on Files SQL statement can be used when connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioae5645003caf4d14bcd05ca4d8f3219e__ATR_syntax"/>

## Syntax

```
ALTER TABLE <remote-schema-name>.<remote-table-name>
    IN FILES_SERVICE { MANUAL | AUTO } REFRESH
```



<a name="loioae5645003caf4d14bcd05ca4d8f3219e__ATR_parameters"/>

## Parameters


<dl>
<dt><b>

*<remote-schema-name\>*

</b></dt>
<dd>

IN FILES\_SERVICE The name of the schema. If a schema name is not provided, the current schema is used.



</dd><dt><b>

*<remote-table-name\>*

</b></dt>
<dd>

The name of the table.



</dd><dt><b>

REFRESH

</b></dt>
<dd>

The refresh mode of the table.


<dl>
<dt><b>

`MANUAL`

</b></dt>
<dd>

Sets the refresh mode to manual, and must be refreshed using the [REFRESH \(Remote\) TABLE Statement for Data Lake Relational Engine \[SQL on Files\]](refresh-remote-table-statement-for-data-lake-relational-engine-sql-on-files-e275657.md).



</dd><dt><b>

`AUTO`

</b></dt>
<dd>

Sets the refresh to automatically occur with every SELECT query on the table.



</dd>
</dl>



</dd>
</dl>



<a name="loioae5645003caf4d14bcd05ca4d8f3219e__ATR_remarks"/>

## Remarks

Refreshing a table includes removing deleted files from the external catalog, adding new files and directories to the catalog, and updating modified files.

> ### Note:  
> If a table is created with the refresh mode set to `MANUAL`, the list of files is only updated by using `REFRESH TABLE` statements. The `REFRESH TABLE` statement is not necessary for tables created with the refresh mode set to `AUTO`. See the [CREATE \(Remote\) TABLE Statement for Data Lake Relational Engine \[SQL on Files\]](create-remote-table-statement-for-data-lake-relational-engine-sql-on-files-beffc07.md) for more information.

Refreshing the table updates the current list of data source files for a SQL on Files remote table by performing a directory scan on all current data sources attached to the remote table. Files added to the underlying source but not yet tracked in the external catalog are not visible when querying the table. A SELECT query failure occurs if there are files tracked in the external catalog that have been deleted or modified in the underlying source.

```
Catalog error:
Request for runtime files for 
table '<table>' version '<internal_version1>' in schema '<schema>' 
does not match current runtime files version: '<internal_version2>'
```



<a name="loioae5645003caf4d14bcd05ca4d8f3219e__section_l3n_psd_j4b"/>

## Privileges

You have been granted the HDL\_FILES\_SERVICE\_ADMIN role.



<a name="loioae5645003caf4d14bcd05ca4d8f3219e__ATR_example"/>

## Examples

The following example sets `REFRESH` to automatic for `ExternalTable1`:

```
ALTER TABLE ExternalSchema1.ExternalTable1 IN FILES_SERVICE
	AUTO REFRESH
```

**Related Information**  


[REFRESH \(Remote\) TABLE Statement for Data Lake Relational Engine \[SQL on Files\]](refresh-remote-table-statement-for-data-lake-relational-engine-sql-on-files-e275657.md "Update the current list of data source files for a SQL on Files remote table by performing a directory scan on all current data sources attached to this remote table.")

[CREATE \(Remote\) TABLE Statement for Data Lake Relational Engine \[SQL on Files\]](create-remote-table-statement-for-data-lake-relational-engine-sql-on-files-beffc07.md "Create a remote table managed by SQL on Files.")

[DROP \(Remote\) TABLE Statement for Data Lake Relational Engine \[SQL on Files\]](drop-remote-table-statement-for-data-lake-relational-engine-sql-on-files-f81d073.md "Drop a remote table from a SQL on Files external catalog.")

[ALTER (Remote) TABLE Statement with REFRESH for Data Lake Relational Engine (SAP HANA DB-Managed) [SQL on Files]](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/ff7b384154d0499594c61f49329dce04.html "Alter the refresh mode of a table.") :arrow_upper_right:

