<!-- loio1e62d1971ef24618818f5c5926cdcd26 -->

# DROP TABLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Removes a table from the database.



<a name="loio1e62d1971ef24618818f5c5926cdcd26__section_fyr_c3p_m5b"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected to SAP HANA database as a SAP HANA database user and using the SAP HANA database REMOTE\_EXECUTE procedure.



```
DROP TABLE [ IF EXISTS ] [ <schema-name>.]<table-name>;
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio1e62d1971ef24618818f5c5926cdcd26__section_yy2_mwj_dzb"/>

## Parameters


<dl>
<dt><b>

IF EXISTS

</b></dt>
<dd>

Use if you do not want an error returned when the DROP statement attempts to remove a database object that does not exist.



</dd>
</dl>



<a name="loio1e62d1971ef24618818f5c5926cdcd26__section_hlt_mwj_dzb"/>

## Remarks

All data in the table is automatically deleted as part of the dropping process. Also, all indexes and keys for the table are dropped by DROP TABLE.

Global temporary tables cannot be dropped unless all users that have referenced the temporary table have disconnected.

DROP TABLE is prevented whenever the statement affects a table that is currently being used by another connection or if the primary table has foreign-key constraints associated with it, including unenforced foreign-key constraints. It is also prevented if the table has an IDENTITY column and IDENTITY\_INSERT is set to that table. To drop the table, you must clear IDENTITY\_INSERT, that is, set IDENTITY\_INSERT to ' ' \(an empty string\), or set to another table name.

A foreign key can have either a nonunique single or a multicolumn HG index. A primary key may have unique single or multicolumn HG indexes. You cannot drop the HG index implicitly created for an existing foreign key, primary key, and unique constraint.



<a name="loio1e62d1971ef24618818f5c5926cdcd26__section_swk_nwj_dzb"/>

## Privileges



### 


<dl>
<dt><b>

Connected to SAP HANA database as a SAP HANA database user and using the SAP HANA database REMOTE\_EXECUTE procedure:

</b></dt>
<dd>

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the SAP HANA database REMOTE\_EXECUTE procedure associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).

-   See [REMOTE\_EXECUTE Guidance and Examples for Executing SQL Statements](remote-execute-guidance-and-examples-for-executing-sql-statements-fd99ac0.md).




</dd>
</dl>



<a name="loio1e62d1971ef24618818f5c5926cdcd26__section_tx1_4wj_dzb"/>

## Side Effects

-   Automatic commit. Clears the Data window in dbisql. DROP TABLE and DROP INDEX close all cursors for the current connection.
-   Local temporary tables are an exception; no commit is performed when one is dropped.



<a name="loio1e62d1971ef24618818f5c5926cdcd26__section_jbr_4wj_dzb"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – supported by SAP Adaptive Server Enterprise



<a name="loio1e62d1971ef24618818f5c5926cdcd26__section_agk_pwj_dzb"/>

## Examples

This example drops the table departments if it exists:

```
DROP IF EXISTS TABLE departments;
```

**Related Information**  


[CREATE TABLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-table-statement-for-data-lake-relational-engine-sap-hana-db-managed-6c3afae.md "Creates a new table in the database or on a remote server.")

[ALTER TABLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](alter-table-statement-for-data-lake-relational-engine-sap-hana-db-managed-593f8b1.md "Modifies a table definition.")

[DROP TABLE Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/0524ea8d6c124d0e8c7bea18021e6c1f.html "Removes a table from the database.") :arrow_upper_right:

