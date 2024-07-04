<!-- loiob23679a94d9f45a4b169f484005f46da -->

# SET SCHEMA Statement for Data Lake Relational Engine

Sets the default schema for the connection



<a name="loiob23679a94d9f45a4b169f484005f46da__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
SET SCHEMA [ <schema_name> ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loiob23679a94d9f45a4b169f484005f46da__set_schema_privileges1"/>

## Privileges



### 

None



<a name="loiob23679a94d9f45a4b169f484005f46da__set_schema_remarks1"/>

## Remarks

When executing a SQL statement that references a database object, if a schema name is not specified, then the current value of the SET SCHEMA statement is cleared. The SET schema remains in effect for the duration of the connection or until reset to another schema name or cleared.



<a name="loiob23679a94d9f45a4b169f484005f46da__set_schema_example1"/>

## Examples

The following example creates a new schema called SCHEMA\_1, and then sets the default schema to it.

```
CREATE SCHEMA SCHEMA1;
```

```
SET SCHEMA SCHEMA1;
```

Table T1 is then created without specifying a schema.

```
CREATE T1 (A INT, B INT);
```

The table is created in the default \(SET\) schema. To query table T1, the following two statements are equivalent:

```
SELECT * FROM T1;
```

```
SELECT * FROM SCHEMA_1.T1;
```

This clears the current SET SCHEMA value in effect, SCHEMA1.

```
SET SCHEMA;
```

**Related Information**  


[CREATE SCHEMA Statement for Data Lake Relational Engine](create-schema-statement-for-data-lake-relational-engine-5e20f75.md "Creates a schema in the current instance.")

[DROP SCHEMA Statement for Data Lake Relational Engine](drop-schema-statement-for-data-lake-relational-engine-0c4b714.md "Removes a schema from the database.")

[SET SCHEMA Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/819f6ce2e6ef4d78ba11c7fcc194ea6e.html "Sets the default schema for the connection") :arrow_upper_right:

