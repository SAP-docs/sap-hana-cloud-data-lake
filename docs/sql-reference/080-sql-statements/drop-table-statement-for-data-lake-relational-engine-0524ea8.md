<!-- loio0524ea8d6c124d0e8c7bea18021e6c1f -->

# DROP TABLE Statement for Data Lake Relational Engine

Removes a table from the database.



<a name="loio0524ea8d6c124d0e8c7bea18021e6c1f__section_azh_5fj_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP TABLE [ IF EXISTS ] [ { <owner> | <schema-name> }.]<table-name>;
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio0524ea8d6c124d0e8c7bea18021e6c1f__drop_table_parm1"/>

## Parameters


<dl>
<dt><b>

IF EXISTS

</b></dt>
<dd>

Use if you do not want an error returned when the DROP statement attempts to remove a database object that does not exist.



</dd>
</dl>



<a name="loio0524ea8d6c124d0e8c7bea18021e6c1f__drop_table_remarks1"/>

## Remarks

All data in the table is automatically deleted as part of the dropping process. Also, all indexes and keys for the table are dropped by DROP TABLE.

Global temporary tables cannot be dropped unless all users that have referenced the temporary table have disconnected.

DROP TABLE is prevented whenever the statement affects a table that is currently being used by another connection or if the primary table has foreign-key constraints associated with it, including unenforced foreign-key constraints. It is also prevented if the table has an IDENTITY column and IDENTITY\_INSERT is set to that table. To drop the table, you must clear IDENTITY\_INSERT, that is, set IDENTITY\_INSERT to ' ' \(an empty string\), or set to another table name.

A foreign key can have either a nonunique single or a multicolumn HG index. A primary key may have unique single or multicolumn HG indexes. You cannot drop the HG index implicitly created for an existing foreign key, primary key, and unique constraint.



<a name="loio0524ea8d6c124d0e8c7bea18021e6c1f__drop_table_priv1"/>

## Privileges



### 

-   Requires one of:

    -   You own the table.
    -   DROP ANY TABLE system privilege
    -   DROP ANY OBJECT system privilege
    -   DROP object-level privilege on the table.
    -   DROP object-level privilege on the schema containing the table if the schema is owned by another user.


See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges.



<a name="loio0524ea8d6c124d0e8c7bea18021e6c1f__drop_table_sideeffect1"/>

## Side Effects

-   Automatic commit. Clears the Data window in dbisql. DROP TABLE and DROP INDEX close all cursors for the current connection.
-   Local temporary tables are an exception; no commit is performed when one is dropped.



<a name="loio0524ea8d6c124d0e8c7bea18021e6c1f__drop_table_standards1"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – supported by SAP Adaptive Server Enterprise



<a name="loio0524ea8d6c124d0e8c7bea18021e6c1f__drop_table_example1"/>

## Examples

This example drops the table departments if it exists:

```
DROP IF EXISTS TABLE departments;
```

**Related Information**  


[CREATE TABLE Statement for Data Lake Relational Engine](create-table-statement-for-data-lake-relational-engine-a619764.md "Creates a new table in the database or on a remote server.")

[ALTER TABLE Statement for Data Lake Relational Engine](alter-table-statement-for-data-lake-relational-engine-39f1ec0.md "Modifies a table definition.")

[DROP TABLE Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/1e62d1971ef24618818f5c5926cdcd26.html "Removes a table from the database.") :arrow_upper_right:

