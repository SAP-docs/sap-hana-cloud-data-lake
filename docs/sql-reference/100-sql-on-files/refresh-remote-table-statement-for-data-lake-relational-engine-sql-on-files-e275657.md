<!-- loioe2756579d6354112a5e5e0f9fe0c2ccb -->

# REFRESH \(Remote\) TABLE Statement for Data Lake Relational Engine \[SQL on Files\]

Update the current list of data source files for a SQL on Files remote table by performing a directory scan on all current data sources attached to this remote table.



<a name="loioe2756579d6354112a5e5e0f9fe0c2ccb__section_fry_b3b_nqb"/>

## Usage

-   This topic is limited to SQL on Files use cases.
-   This SQL on Files SQL statement can be used when connected directly to data lake Relational Engine as a data lake Relational Engine user.



> ### Note:  
> The REFRESH TABLE statement is only applicable to SQL on Files virtual tables and is not recognized in other table types.



<a name="loioe2756579d6354112a5e5e0f9fe0c2ccb__RT_syntax"/>

## Syntax

```
REFRESH TABLE [ <owner> .]<virtual-table-name>[,... ] IN FILES_SERVICE;
```



<a name="loioe2756579d6354112a5e5e0f9fe0c2ccb__RT_parameters"/>

## Parameters


<dl>
<dt><b>

*<owner\>*

</b></dt>
<dd>

The owner of the table.



</dd><dt><b>

*<virtual-table-name\>*

</b></dt>
<dd>

The virtual table defined on SQL on Files remote tables.

The `REFRESH TABLE` statement can specify SQL on Files remote tables, or virtual tables defined on SQL on Files remote tables. When specifying a list of virtual tables, the statement is equivalent to a list of remote tables defining the virtual tables.



</dd>
</dl>



<a name="loioe2756579d6354112a5e5e0f9fe0c2ccb__RT_remarks"/>

## Remarks

Refreshing a table includes removing deleted files from the external catalog, adding new files and directories to the catalog, and updating modified files. Refreshing the table updates the current list of data source files for a SQL on Files remote table by performing a directory scan on all current data sources attached to the remote table.

A table with the refresh mode set to `MANUAL` only updates the list of files by using `REFRESH TABLE` statements. SQL on Files ignores newly added files and returns an error if existing files have changed since the last refresh. When the underlying file content is unchanging, or changes at known intervals, using a `MANUAL` refresh provides a performance benefit as SQL on Files doesn't have to check for new or changed files each time a query is executed.

> ### Note:  
> The `REFRESH TABLE` statement is not necessary for tables created with the refresh mode set to `AUTO`. See the [CREATE \(Remote\) TABLE Statement for Data Lake Relational Engine \[SQL on Files\]](create-remote-table-statement-for-data-lake-relational-engine-sql-on-files-beffc07.md) for more information.

Files that have been added to the object store but have not been registered in the SQL on Files catalog by a refresh statement are not visible when querying the table. A SELECT query failure occurs if there are files tracked in the catalog that have been deleted or modified in the underlying source.

```
Catalog error:
Request for runtime files for 
table '<table>' version '<internal_version1>' in schema '<schema>' 
does not match current runtime files version: '<internal_version2>'
```



<a name="loioe2756579d6354112a5e5e0f9fe0c2ccb__section_l3n_psd_j4b"/>

## Privileges

You have been granted the HDL\_FILES\_SERVICE\_ADMIN role.



<a name="loioe2756579d6354112a5e5e0f9fe0c2ccb__RT_example"/>

## Examples

The following example creates the virtual table `virtualTable1` and sets the refresh mode to `MANUAL`:

```
CREATE EXISTING virtualTable1 AT 'SOF..ExternalSchema1.ExternalTable1'
	MANUAL REFRESH;
```

The following example manually refreshes `ExternalTable1` to update the list of datasources:

```
REFRESH TABLE ExternalSchema1.ExternalTable1 IN FILES_SERVICE;
```

**Related Information**  


[ALTER \(Remote\) TABLE Statement with REFRESH for Data Lake Relational Engine \[SQL on Files\]](alter-remote-table-statement-with-refresh-for-data-lake-relational-engine-sql-on-files-ae56450.md "Alter the refresh mode of a table.")

[CREATE \(Remote\) TABLE Statement for Data Lake Relational Engine \[SQL on Files\]](create-remote-table-statement-for-data-lake-relational-engine-sql-on-files-beffc07.md "Create a remote table managed by SQL on Files.")

[REFRESH (Remote) TABLE Statement for Data Lake Relational Engine (SAP HANA DB-Managed) \[SQL on Files\]](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/054b15028fcc43dba2b047f8dbe6b42b.html "Update the current list of data source files for a SQL on Files remote table by performing a directory scan on all current data sources attached to this remote table.") :arrow_upper_right:

