<!-- loio5e20f75f3b664f02b1d92f4a22999105 -->

# CREATE SCHEMA Statement for Data Lake Relational Engine

Creates a schema in the current instance.



<a name="loio5e20f75f3b664f02b1d92f4a22999105__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
CREATE SCHEMA [ <owner>.]<schema_name>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio5e20f75f3b664f02b1d92f4a22999105__create_schema_parm1"/>

## Parameters


<dl>
<dt><b>

*<owner\>*

</b></dt>
<dd>

Specifies who owns the schema. If none specified, the current user becomes the owner. An owner must be a user. It cannot be a role or another schema.



</dd><dt><b>

*<schema\_name\>*

</b></dt>
<dd>

Specifies the name of the schema. The name must be unique for the database. Multiple users cannot have the same schema name and the schema name cannot be the same as any user or role.



</dd>
</dl>



<a name="loio5e20f75f3b664f02b1d92f4a22999105__create_schema_remarks1"/>

## Remarks

When referencing an object in a schema, *<owner\>* is not included in the syntax, regardless of who owns the schema. For example, table T1 exists in SCHEMA\_1. You are USER1 and you own SCHEMA\_1. Table T2 exists in SCHEMA\_2. USER2 owns SCHEMA\_2. The syntax to query tables T1 and T2 is as follows:

**Correct Syntax:**

```
SELECT * FROM SCHEMA_1.T1;
SELECT * FROM SCHEMA_2.T2;
```

**Incorrect Syntax:**

```
SELECT * FROM USER1.SCHEMA_1.T1;
SELECT * FROM USER2.SCHEMA_2.T2;
```



<a name="loio5e20f75f3b664f02b1d92f4a22999105__create_schema_privilege1"/>

## Privileges



### 

-   To create a schema you own requires the CREATE DATABASE SCHEMA system privilege.
-   To create a schema owned by another user, you must have one of the following:
    -   CREATE ANY DATABASE SCHEMA system privilege
    -   CREATE ANY OBJECT system privilege




## Examples

This example creates the schema named my\_schema, owned by the current user.

```
CREATE SCHEMA my_schema;
```

This example creates the schema named my\_schema1 that is owned by user\_1.

```
CREATE SCHEMA user_1.my_schema1;
```

**Related Information**  


[DROP SCHEMA Statement for Data Lake Relational Engine](drop-schema-statement-for-data-lake-relational-engine-0c4b714.md "Removes a schema from the database.")

[SET SCHEMA Statement for Data Lake Relational Engine](set-schema-statement-for-data-lake-relational-engine-b23679a.md "Sets the default schema for the connection")

[CREATE SCHEMA for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/7988025f66db454aae19ae0c7a4fe042.html "Creates a schema in the current instance.") :arrow_upper_right:

