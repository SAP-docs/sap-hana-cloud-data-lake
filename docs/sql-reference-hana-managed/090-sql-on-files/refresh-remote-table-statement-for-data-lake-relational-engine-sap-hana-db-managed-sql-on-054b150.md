<!-- loio054b15028fcc43dba2b047f8dbe6b42b -->

# REFRESH \(Remote\) TABLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\) \[SQL on Files\]

Update the current list of data source files for a SQL on Files remote table by performing a directory scan on all current data sources attached to this remote table.



> ### Restriction:  
> This topic is limited to SQL on Files use cases.
> 
> This data lake Relational Engine \(SAP HANA DB-Managed\) SQL on Files SQL statement can be used as follows:
> 
> -   When connected to SAP HANA database as a SAP HANA database user.
> 
> -   Using the REMOTE\_EXECUTE procedure. See [REMOTE\_EXECUTE Usage Examples for Executing SQL Statements](../030-sql-statements/remote-execute-usage-examples-for-executing-sql-statements-fd99ac0.md).



## Syntax

```
REFRESH TABLE [ <owner> .]<virtual-table-name>[,... ] IN FILES_SERVICE
```



## Parameters

 *<owner\>*
 :   The owner of the table.

  *<virtual-table-name\>*
 :   The virtual table defined on SQL on Files remote tables.

    The `REFRESH TABLE` statement can specify SQL on Files remote tables, or virtual tables defined on SQL on Files remote tables. When specifying a list of virtual tables, the statement is equivalent to a list of remote tables defining the virtual tables.

 

## Remarks

Refreshing a table includes removing deleted files from the external catalog, adding new files and directories to the catalog, and updating modified files. Refreshing the table updates the current list of data source files for a SQL on Files remote table by performing a directory scan on all current data sources attached to the remote table.

A table with the refresh mode set to `MANUAL` only updates the list of files by using `REFRESH TABLE` statements. SQL on Files ignores newly added files and returns an error if existing files have changed since the last refresh. When the underlying file content is unchanging, or changes at known intervals, using a `MANUAL` refresh provides a performance benefit as SQL on Files doesn't have to check for new or changed files each time a query is executed.

> ### Note:  
> The `REFRESH TABLE` statement is not necessary for tables created with the refresh mode set to `AUTO`. See the [CREATE (Remote) TABLE Statement for Data Lake Relational Engine [SQL on Files]](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/beffc07c515540088d372197c9eee191.html "Create a remote table managed by SQL on Files.") :arrow_upper_right: for more information.

Files that have been added to the object store but have not been registered in the SQL on Files catalog by a refresh statement are not visible when querying the table. A SELECT query failure occurs if there are files tracked in the catalog that have been deleted or modified in the underlying source.

```
Catalog error:
Request for runtime files for 
table '<table>' version '<internal_version1>' in schema '<schema>' 
does not match current runtime files version: '<internal_version2>'
```



<a name="loio054b15028fcc43dba2b047f8dbe6b42b__section_l3n_psd_j4b"/>

## Privileges

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



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


[REMOTE\_EXECUTE Usage Examples for Executing SQL Statements](../030-sql-statements/remote-execute-usage-examples-for-executing-sql-statements-fd99ac0.md "Execute a data lake Relational Engine SQL statement by embedding the statement in the REMOTE_EXECUTE procedure.")

[ALTER \(Remote\) TABLE Statement with REFRESH for Data Lake Relational Engine \(SAP HANA DB-Managed\) \[SQL on Files\]](alter-remote-table-statement-with-refresh-for-data-lake-relational-engine-sap-hana-db-man-ff7b384.md "Alter the refresh mode of a table.")

[CREATE \(Remote\) TABLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\) \[SQL on Files\]](create-remote-table-statement-for-data-lake-relational-engine-sap-hana-db-managed-sql-on-24e694b.md "Create a remote table managed by SQL on Files.")

[DROP \(Remote\) TABLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\) \[SQL on Files\]](drop-remote-table-statement-for-data-lake-relational-engine-sap-hana-db-managed-sql-on-fi-ca1e55d.md "Drop a remote table from a SQL on Files external catalog.")

[REFRESH (Remote) TABLE Statement for Data Lake Relational Engine [SQL on Files]](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/e2756579d6354112a5e5e0f9fe0c2ccb.html "Update the current list of data source files for a SQL on Files remote table by performing a directory scan on all current data sources attached to this remote table.") :arrow_upper_right:

