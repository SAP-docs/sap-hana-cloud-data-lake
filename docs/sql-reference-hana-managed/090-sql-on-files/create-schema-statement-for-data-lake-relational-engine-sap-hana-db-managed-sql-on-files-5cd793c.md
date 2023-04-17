<!-- loio5cd793c72fd34f4bb337698fa11ea3d0 -->

# CREATE SCHEMA Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\) \[SQL on Files\]

Create a schema, which is a collection of tables, managed by SQL on Files.



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
CREATE SCHEMA <remote-schema-name> IN FILES_SERVICE
```



## Parameters

 *<remote-schema-name\>*
 :   The name of the new schema. If the schema already exists in SQL on Files, an error is returned.

 

## Remarks

The SQL on Files external catalog stores the remote schema definition. This remote schema will have a collection of remote tables, and each remote table must belong to an existing remote schema.



<a name="loio5cd793c72fd34f4bb337698fa11ea3d0__section_qdy_qmb_nqb"/>

## Privileges

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



## Examples

The following statement creates the schema `Factory`:

```
CREATE SCHEMA Factory IN FILES_SERVICE;
```

**Related Information**  


[REMOTE\_EXECUTE Usage Examples for Executing SQL Statements](../030-sql-statements/remote-execute-usage-examples-for-executing-sql-statements-fd99ac0.md "Execute a data lake Relational Engine SQL statement by embedding the statement in the REMOTE_EXECUTE procedure.")

[CREATE SCHEMA Statement for Data Lake Relational Engine [SQL on Files]](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/af3fb5b713f34db2aaa8efbf0c2a9e45.html "Create a schema, which is a collection of tables, managed by SQL on Files.") :arrow_upper_right:
