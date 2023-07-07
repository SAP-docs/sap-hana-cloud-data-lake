<!-- loioca1e55df6c6f4e0aa381832e5504a4b9 -->

# DROP \(Remote\) TABLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\) \[SQL on Files\]

Drop a remote table from a SQL on Files external catalog.



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
DROP TABLE <remote-schema-name>.<remote-table-name> IN FILES_SERVICE
```



## Parameters


<dl>
<dt><b>

*<remote-schema-name\>*

</b></dt>
<dd>

The schema of the table. *<remote-schema-name\>* must be provided.



</dd><dt><b>

*<remote-table-name\>*

</b></dt>
<dd>

The name of the table to be deleted.



</dd>
</dl>



<a name="loioca1e55df6c6f4e0aa381832e5504a4b9__section_wjs_t4b_nqb"/>

## Privileges

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



## Examples

The following statement drops the table `ExternalTable1`:

```
DROP TABLE ExternalSchema1.ExternalTable1 IN FILES_SERVICE;
```

**Related Information**  


[REMOTE\_EXECUTE Usage Examples for Executing SQL Statements](../030-sql-statements/remote-execute-usage-examples-for-executing-sql-statements-fd99ac0.md "Execute a data lake Relational Engine SQL statement by embedding the statement in the REMOTE_EXECUTE procedure.")

[CREATE \(Remote\) TABLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\) \[SQL on Files\]](create-remote-table-statement-for-data-lake-relational-engine-sap-hana-db-managed-sql-on-24e694b.md "Create a remote table managed by SQL on Files.")

[ALTER \(Remote\) TABLE Statement with REFRESH for Data Lake Relational Engine \(SAP HANA DB-Managed\) \[SQL on Files\]](alter-remote-table-statement-with-refresh-for-data-lake-relational-engine-sap-hana-db-man-ff7b384.md "Alter the refresh mode of a table.")

[REFRESH \(Remote\) TABLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\) \[SQL on Files\]](refresh-remote-table-statement-for-data-lake-relational-engine-sap-hana-db-managed-sql-on-054b150.md "Update the current list of data source files for a SQL on Files remote table by performing a directory scan on all current data sources attached to this remote table.")

[DROP (Remote) TABLE Statement for Data Lake Relational Engine [SQL on Files]](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/f81d073adf494841b1f7ece9ed0e7266.html "Drop a remote table from a SQL on Files external catalog.") :arrow_upper_right:

