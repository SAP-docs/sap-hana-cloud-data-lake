<!-- loioff7b384154d0499594c61f49329dce04 -->

# ALTER \(Remote\) TABLE Statement with REFRESH for Data Lake Relational Engine \(SAP HANA DB-Managed\) \[SQL on Files\]

Alter the refresh mode of a table.



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
ALTER TABLE <remote-schema-name>.<remote-table-name>
    IN FILES_SERVICE { MANUAL | AUTO } REFRESH
```



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

Sets the refresh mode to manual, and must be refreshed using the [REFRESH (Remote) TABLE Statement for Data Lake Relational Engine [SQL on Files]](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/e2756579d6354112a5e5e0f9fe0c2ccb.html "Update the current list of data source files for a SQL on Files remote table by performing a directory scan on all current data sources attached to this remote table.") :arrow_upper_right:.



</dd><dt><b>

`AUTO`

</b></dt>
<dd>

Sets the refresh to automatically occur with every SELECT query on the table.



</dd>
</dl>



</dd>
</dl>



## Remarks

Refreshing a table includes removing deleted files from the external catalog, adding new files and directories to the catalog, and updating modified files.

> ### Note:  
> If a table is created with the refresh mode set to `MANUAL`, the list of files is only updated by using `REFRESH TABLE` statements. The `REFRESH TABLE` statement is not necessary for tables created with the refresh mode set to `AUTO`. See the [CREATE (Remote) TABLE Statement for Data Lake Relational Engine [SQL on Files]](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/beffc07c515540088d372197c9eee191.html "Create a remote table managed by SQL on Files.") :arrow_upper_right: for more information.

Refreshing the table updates the current list of data source files for a SQL on Files remote table by performing a directory scan on all current data sources attached to the remote table. Files added to the underlying source but not yet tracked in the external catalog are not visible when querying the table. A SELECT query failure occurs if there are files tracked in the external catalog that have been deleted or modified in the underlying source.

```
Catalog error:
Request for runtime files for 
table '<table>' version '<internal_version1>' in schema '<schema>' 
does not match current runtime files version: '<internal_version2>'
```



<a name="loioff7b384154d0499594c61f49329dce04__section_l3n_psd_j4b"/>

## Privileges

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



## Examples

The following example sets `REFRESH` to automatic for `ExternalTable1`:

```
ALTER TABLE ExternalSchema1.ExternalTable1 IN FILES_SERVICE
	AUTO REFRESH
```

**Related Information**  


[REMOTE\_EXECUTE Usage Examples for Executing SQL Statements](../030-sql-statements/remote-execute-usage-examples-for-executing-sql-statements-fd99ac0.md "Execute a data lake Relational Engine SQL statement by embedding the statement in the REMOTE_EXECUTE procedure.")

[REFRESH \(Remote\) TABLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\) \[SQL on Files\]](refresh-remote-table-statement-for-data-lake-relational-engine-sap-hana-db-managed-sql-on-054b150.md "Update the current list of data source files for a SQL on Files remote table by performing a directory scan on all current data sources attached to this remote table.")

[CREATE \(Remote\) TABLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\) \[SQL on Files\]](create-remote-table-statement-for-data-lake-relational-engine-sap-hana-db-managed-sql-on-24e694b.md "Create a remote table managed by SQL on Files.")

[DROP \(Remote\) TABLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\) \[SQL on Files\]](drop-remote-table-statement-for-data-lake-relational-engine-sap-hana-db-managed-sql-on-fi-ca1e55d.md "Drop a remote table from a SQL on Files external catalog.")

[ALTER (Remote) TABLE Statement with REFRESH for Data Lake Relational Engine [SQL on Files]](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/ae5645003caf4d14bcd05ca4d8f3219e.html "Alter the refresh mode of a table.") :arrow_upper_right:

