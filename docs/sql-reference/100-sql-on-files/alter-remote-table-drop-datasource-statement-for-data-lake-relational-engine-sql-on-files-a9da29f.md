<!-- loioa9da29fdd7a141eea66117b22cca84c7 -->

# ALTER \(Remote\) TABLE DROP DATASOURCE Statement for Data Lake Relational Engine \[SQL on Files\]

Remove a data source from a SQL on Files table.



> ### Restriction:  
> This topic is limited to SQL on Files use cases.
> 
> This SQL on Files SQL statement can be used when connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa9da29fdd7a141eea66117b22cca84c7__ATDD_syntax"/>

## Syntax

```
ALTER TABLE <remote-schema-name>.<remote-table-name> IN FILES_SERVICE 
	DROP DATASOURCE { <datasource-name> | ALL }
```



<a name="loioa9da29fdd7a141eea66117b22cca84c7__ATDD_parameters"/>

## Parameters

 *<remote-schema-name\>*
 :   The name of the schema. If a schema name is not provided, the current schema is used.

  *<remote-table-name\>*
 :   The name of the table.

  *<datasource-name\>*
 :   The name of the datasource being dropped.

 

## Privileges

You have been granted the HDL\_FILES\_SERVICE\_ADMIN role or the ALTER TABLE FILES SERVICE privilege.



<a name="loioa9da29fdd7a141eea66117b22cca84c7__ATDD_example"/>

## Examples

The following example drops datasource `DS1` from `ExternalTable1`:

```
ALTER TABLE ExternalSchema1.ExternalTable1 IN FILES_SERVICE 
	DROP DATASOURCE DS1
```

**Related Information**  


[ALTER \(Remote\) TABLE ADD DATASOURCE Statement for Data Lake Relational Engine \[SQL on Files\]](alter-remote-table-add-datasource-statement-for-data-lake-relational-engine-sql-on-files-65c9d8f.md "Attach an external data source, such as a file or directory, to a SQL on Files remote table.")

[ALTER (Remote) TABLE DROP DATASOURCE Statement for Data Lake Relational Engine (SAP HANA DB-Managed) [SQL on Files]](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/1e570afca5014f4098f36be8db1129b6.html "Remove a data source from a SQL on Files table.") :arrow_upper_right:
