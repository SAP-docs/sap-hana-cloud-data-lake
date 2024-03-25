<!-- loio7988025f66db454aae19ae0c7a4fe042 -->

# CREATE SCHEMA for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Creates a schema in the current instance.



<a name="loio7988025f66db454aae19ae0c7a4fe042__section_gqj_hjr_btb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected to SAP HANA database as a SAP HANA database user..



```
CREATE SCHEMA [ <owner>.]<schema_name>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio7988025f66db454aae19ae0c7a4fe042__section_wgv_jlr_btb"/>

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



<a name="loio7988025f66db454aae19ae0c7a4fe042__section_qz3_klr_btb"/>

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



<a name="loio7988025f66db454aae19ae0c7a4fe042__section_iyk_2ds_wwb"/>

## Privileges



### 

To use REMOTE\_EXECUTE requires one of the following:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the SAP HANA database REMOTE\_EXECUTE procedure associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).

**Related Information**  


[DROP SCHEMA Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](drop-schema-statement-for-data-lake-relational-engine-sap-hana-db-managed-2529cf1.md "")

