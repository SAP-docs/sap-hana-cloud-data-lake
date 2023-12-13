<!-- loio1e570afca5014f4098f36be8db1129b6 -->

# ALTER \(Remote\) TABLE DROP DATASOURCE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\) \[SQL on Files\]

Remove a data source from a SQL on Files table.



<a name="loio1e570afca5014f4098f36be8db1129b6__section_inj_b3b_nqb"/>

## Usage

-   This topic is limited to SQL on Files use cases.

-   This data lake Relational Engine \(SAP HANA DB-Managed\) SQL on Files SQL statement can be used as follows:

    -   Connected to SAP HANA database as a SAP HANA database user and using the SAP HANA database REMOTE\_EXECUTE procedure.
    -   Using the REMOTE\_EXECUTE procedure. See [REMOTE\_EXECUTE Guidance and Examples for Executing SQL Statements](../030-sql-statements/remote-execute-guidance-and-examples-for-executing-sql-statements-fd99ac0.md).





<a name="loio1e570afca5014f4098f36be8db1129b6__section_f45_23b_nqb"/>

## Syntax

```
ALTER TABLE <remote-schema-name>.<remote-table-name> IN FILES_SERVICE 
	DROP DATASOURCE { <datasource-name> | ALL };
```



<a name="loio1e570afca5014f4098f36be8db1129b6__section_iww_23b_nqb"/>

## Parameters


<dl>
<dt><b>

*<remote-schema-name\>*

</b></dt>
<dd>

The name of the schema. If a schema name is not provided, the current schema is used.



</dd><dt><b>

*<remote-table-name\>*

</b></dt>
<dd>

The name of the table.



</dd><dt><b>

*<datasource-name\>*

</b></dt>
<dd>

The name of the datasource being dropped.



</dd>
</dl>



<a name="loio1e570afca5014f4098f36be8db1129b6__section_srk_zhb_nqb"/>

## Privileges

To use REMOTE\_EXECUTE requires one of the following:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the SAP HANA database REMOTE\_EXECUTE procedure associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



## Examples

The following example drops datasource `DS1` from `ExternalTable1`:

```
ALTER TABLE ExternalSchema1.ExternalTable1 IN FILES_SERVICE 
	DROP DATASOURCE DS1;
```

**Related Information**  


[REMOTE\_EXECUTE Guidance and Examples for Executing SQL Statements](../030-sql-statements/remote-execute-guidance-and-examples-for-executing-sql-statements-fd99ac0.md "To run data lake Relational Engine SQL statements using the SAP HANA database REMOTE_EXECUTE or REMOTE_EXECUTE_DDL procedure, you embed the SQL syntax within the procedure.")

[ALTER \(Remote\) TABLE ADD DATASOURCE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\) \[SQL on Files\]](alter-remote-table-add-datasource-statement-for-data-lake-relational-engine-sap-hana-db-m-e6e7243.md "Attach an external data source, such as a file or directory, to a SQL on Files remote table.")

[ALTER (Remote) TABLE DROP DATASOURCE Statement for Data Lake Relational Engine \[SQL on Files\]](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a9da29fdd7a141eea66117b22cca84c7.html "Remove a data source from a SQL on Files table.") :arrow_upper_right:

