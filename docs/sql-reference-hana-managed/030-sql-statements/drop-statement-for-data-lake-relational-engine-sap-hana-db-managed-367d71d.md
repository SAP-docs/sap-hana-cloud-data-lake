<!-- loio367d71dcf7dc49d180e1872c19bf8188 -->

# DROP Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Removes objects from the database.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Executing SQL Statements](remote-execute-usage-examples-for-executing-sql-statements-fd99ac0.md).



```
DROP
   { [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) INDEX [ IF EXISTS ] [ [/pandoc/div/div/horizontalrule/codeblock/span/span/span
     {""}) [/pandoc/div/div/horizontalrule/codeblock/span/span/span/varname
     {"varname"}) <schema-name> (varname] (span].][/pandoc/div/div/horizontalrule/codeblock/span/span/varname
     {"varname"}) <table-name> (varname].][/pandoc/div/div/horizontalrule/codeblock/span/span/varname
     {"varname"}) <index-name> (varname] (span]
   | [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) TABLE [ IF EXISTS ] [ [/pandoc/div/div/horizontalrule/codeblock/span/span/span
     {""}) [/pandoc/div/div/horizontalrule/codeblock/span/span/span/varname
     {"varname"}) <schema-name> (varname] (span].][/pandoc/div/div/horizontalrule/codeblock/span/span/varname
     {"varname"}) <table-name> (varname] (span]
   | [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) VIEW [ IF EXISTS ] [ [/pandoc/div/div/horizontalrule/codeblock/span/span/span
     {""}) [/pandoc/div/div/horizontalrule/codeblock/span/span/span/varname
     {"varname"}) <schema-name> (varname] (span].][/pandoc/div/div/horizontalrule/codeblock/span/span/varname
     {"varname"}) <view-name> (varname] (span]
   | [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) MATERIALIZED VIEW [ IF EXISTS ] [ [/pandoc/div/div/horizontalrule/codeblock/span/span/span
     {""}) [/pandoc/div/div/horizontalrule/codeblock/span/span/span/varname
     {"varname"}) <schema-name> (varname] (span].][/pandoc/div/div/horizontalrule/codeblock/span/span/varname
     {"varname"}) <mat-view-name> (varname] (span][/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) 
   | SCHEMA [/pandoc/div/div/horizontalrule/codeblock/span/span/varname
     {"varname"}) <schema_name> (varname] [ RESTRICT ] (span]
   }
```



<a name="loio367d71dcf7dc49d180e1872c19bf8188__IQ_Parameters"/>

## Parameters

 IF EXISTS
 :   Use if you do not want an error returned when the DROP statement attempts to remove a database object that does not exist.

  SCHEMA
 :   If you drop a schema, then any schema synonym that references it is also dropped. You cannot drop a user if they own a schema.

  RESTRICT
 :   RESTRICT drops the schema, but only when there are no objects in it. If there are still objects in the schema, then an error is returned.

  INDEX
 :   DROP INDEX deletes any explicitly created index. It deletes an implicitly created index only if there are no unique or foreign-key constraints or associated primary key.

    You can't drop an index when the statement affects a table that is currently being used by another connection.

    For a nonunique HG index, DROP INDEX fails if an associated unenforced foreign key exists.

    > ### Caution:  
    > Do not delete views owned by the DBO user. Deleting such views or changing them into tables might cause problems.

  TABLE
 :   DROP TABLE is prevented whenever the statement affects a table that is currently being used by another connection or if the primary table has foreign-key constraints associated with it, including unenforced foreign-key constraints. It is also prevented if the table has an IDENTITY column and IDENTITY\_INSERT is set to that table. To drop the table, you must clear IDENTITY\_INSERT, that is, set IDENTITY\_INSERT to ' ' \(an empty string\), or set to another table name.

    A foreign key can have either a nonunique single or a multicolumn HG index. A primary key may have unique single or multicolumn HG indexes. You cannot drop the HG index implicitly created for an existing foreign key, primary key, and unique constraint.

    The four initial dbspaces are SYSTEM, IQ\_SYSTEM\_MAIN, IQ\_SYSTEM\_TEMP, and IQ\_SYSTEM\_MSG. You cannot drop these initial dbspaces, but you may drop dbspaces from the IQ main store or catalog store, which may contain multiple dbspaces, as long as at least one dbspace remains with readwrite mode.

  MATERIALIZED VIEW
 :   All data in the table is automatically deleted as part of the dropping process. All indexes and keys for the materialized view are dropped as well.

    Use the IF EXISTS clause if you do not want an error returned when the DROP MATERIALIZED VIEW statement attempts to remove a materialized view that does not exist.

    You cannot execute a DROP MATERIALIZED VIEW statement on an object that is currently being used by another connection.

    Executing a DROP MATERIALIZED VIEW statement changes the status of all dependent regular views to INVALID. To determine view dependencies before dropping a materialized view, use the sa\_dependent\_views system procedure.

 

<a name="loio367d71dcf7dc49d180e1872c19bf8188__IQ_Usage"/>

## Remarks

DROP removes the definition of the indicated database structure. If the structure is a table, all data in the table is automatically deleted as part of the dropping process. All indexes and keys for the table are also dropped by DROP TABLE.

Global temporary tables cannot be dropped unless all users that have referenced the temporary table have disconnected.



<a name="loio367d71dcf7dc49d180e1872c19bf8188__section_sb5_l3x_wwb"/>

## Privileges



### 

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio367d71dcf7dc49d180e1872c19bf8188__IQ_Side_Effects"/>

## Side Effects

-   Automatic commit. Clears the Data window in dbisql. DROP TABLE and DROP INDEX close all cursors for the current connection.
-   Local temporary tables are an exception; no commit is performed when one is dropped.
-   Automatic commit occurs for DROP MATERIALIZED VIEW. Commit occurs for DROP MATERIALIZED VIEW IF EXISTS only when the view exists.

    If the materialized view had been populated, DROP MATERIALIZED VIEW will trigger an automatic checkpoint. Closes all cursors for the current connection.

    When a view is dropped, all procedures and triggers are unloaded from memory, so that any procedure or trigger that references the view reflects the fact that the view does not exist. The unloading and loading of procedures and triggers can affect performance if you are regularly dropping and creating views.




<a name="loio367d71dcf7dc49d180e1872c19bf8188__IQ_Standards"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – supported by SAP Adaptive Server Enterprise



<a name="loio367d71dcf7dc49d180e1872c19bf8188__IQ_Examples"/>

## Examples

The following example drop the Departments table from the database:

```
DROP TABLE Departments
```

The following example drop the emp\_dept view from the database:

```
DROP VIEW emp_dept
```

The following example drops a fictitious materialized view, MyMatView, from the database.

```
DROP MATERIALIZED VIEW MyMatView;
```

The following example drops the index DEPARTMENTS\_INDEX1 from the database:

```
DROP INDEX DEPARTMENTS_INDEX1;
```

The following example drops the view EMP\_DEPT\_VIEWS from the database.

```
DROP VIEW EMP_DEPT_VIEWS;
```

**Related Information**  


[ALTER TABLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](alter-table-statement-for-data-lake-relational-engine-sap-hana-db-managed-593f8b1.md "Modifies a table definition.")

[CREATE TABLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-table-statement-for-data-lake-relational-engine-sap-hana-db-managed-6c3afae.md "Creates a new table in the database or on a remote server.")

[ALTER MATERIALIZED VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](alter-materialized-view-statement-for-data-lake-relational-engine-sap-hana-db-managed-8169459.md "Alters a materialized view.")

[CREATE MATERIALIZED VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-materialized-view-statement-for-data-lake-relational-engine-sap-hana-db-managed-816c0ee.md "Creates a materialized view.")

[ALTER INDEX Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](alter-index-statement-for-data-lake-relational-engine-sap-hana-db-managed-daf745a.md "Renames indexes in base or global temporary tables, foreign key role names of indexes and foreign keys explicitly created by a user, or changes the clustered nature of an index on a catalog store table. You can't rename indexes created to enforce key constraints.")

[CREATE INDEX Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-index-statement-for-data-lake-relational-engine-sap-hana-db-managed-afc9ba6.md "Creates an index on a specified table, or pair of tables. Once an index is created, it is never referenced in a SQL statement again except to delete it using the DROP INDEX statement.")

[ALTER VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](alter-view-statement-for-data-lake-relational-engine-sap-hana-db-managed-6ef5483.md "Replaces a view definition with a modified version.")

[CREATE VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-view-statement-for-data-lake-relational-engine-sap-hana-db-managed-4d41128.md "Creates a view on the database. Views are used to give a different perspective on the data even though it is not stored that way.")

[DROP Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a61c216b84f21015baa181c153419bbb.html "Removes objects from the database.") :arrow_upper_right:

