<!-- loioa627e60884f21015aecdf8c062900097 -->

# TRUNCATE Statement for Data Lake Relational Engine

Deletes all rows from a table ormaterialized view without deleting the table definition.



<a name="loioa627e60884f21015aecdf8c062900097__section_azh_5fj_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
TRUNCATE 
   { TABLE [ { <owner> | <schema-name> }.]<table-name>
      [ { PARTITION <partition-name> | SUBPARTITION <subpartition-name> } ]
   | MATERIALIZED VIEW [ { <owner> | <schema-name> }.]<materialized-view-name> }
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa627e60884f21015aecdf8c062900097__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

PARTITION

</b></dt>
<dd>

Specifies which partition to truncate, and does not affect data in other partitions.



</dd><dt><b>

SUBPARTITION

</b></dt>
<dd>

Truncates tables partitioned by a composite partitioning scheme.



</dd>
</dl>



<a name="loioa627e60884f21015aecdf8c062900097__truncate_privileges1"/>

## Privileges



### 

To TRUNCATE a table or materialized view requires one of:

-   You own the object
-   TRUNCATE ANY TABLE system privilege
-   ALTER ANY TABLE system privilege
-   ALTER ANY OBJECT system privilege
-   TRUNCATE object-level privilege on the object
-   TRUNCATE object-level privilege on the schema containing the object if the schema is owned by another user.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges.

For both temporary and base tables, you can execute TRUNCATE TABLE while other users have read access to the table. This behavior differs from SAP SQL Anywhere, which requires exclusive access to truncate a base table. Data lake Relational Engine table versioning ensures that TRUNCATE TABLE can occur while other users have read access; however, the version of the table these users see depends on when the read and write transactions commit.



<a name="loioa627e60884f21015aecdf8c062900097__truncate_remarks1"/>

## Remarks



### 

TRUNCATE is equivalent to a DELETE statement without a WHERE clause, except that each individual row deletion is not entered into the transaction log. After a TRUNCATE TABLE statement, the table structure and all of the indexes continue to exist until you issue a DROP TABLE statement. The column definitions and constraints remain intact, and permissions remain in effect.

The TRUNCATE statement is entered into the transaction log as a single statement, like data definition statements. Each deleted row is not entered into the transaction log.

> ### Note:  
> If the table you are truncating contains an identity column, the TRUNCATE statement does **not** reset the identity number sequence. If you need to reset the identity number sequence, call the stored procedure sp\_iq\_reset\_identity. See [sp\_iq\_reset\_identity Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iq-reset-identity-procedure-for-data-lake-relational-engine-a5b4402.md).



<a name="loioa627e60884f21015aecdf8c062900097__truncate_sideeffect1"/>

## Side Effects

-   When you truncate a materialized view, you change the status of the view to uninitialized.

-   A COMMIT is performed before and after a TRUNCATE statement is executed.




<a name="loioa627e60884f21015aecdf8c062900097__truncate_standards"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – supported by SAP Adaptive Server Enterprise



<a name="loioa627e60884f21015aecdf8c062900097__IQ_Examples"/>

## Examples

The following example delete all rows from the Sale table:

```
TRUNCATE TABLE Sale
```

**Related Information**  


[TRUNCATE Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/817f97c16ce21014ba1dcdaaf046de69.html "Deletes all rows from a materialized view without deleting the table definition.") :arrow_upper_right:

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[REVOKE Object-Level Privilege Statement for Data Lake Relational Engine](revoke-object-level-privilege-statement-for-data-lake-relational-engine-a3e7af2.md "Removes object-level privileges that were given using the GRANT statement.")

[DELETE Statement for Data Lake Relational Engine](delete-statement-for-data-lake-relational-engine-a61b555.md "Deletes all the rows from the named table that satisfy the search condition. If no WHERE clause is specified, all rows from the named table are deleted.")

[ALTER MATERIALIZED VIEW Statement for Data Lake Relational Engine](alter-materialized-view-statement-for-data-lake-relational-engine-d958953.md "Alters a materialized view.")

[CREATE MATERIALIZED VIEW Statement for Data Lake Relational Engine](create-materialized-view-statement-for-data-lake-relational-engine-d5c757e.md "Creates a materialized view.")

[REFRESH MATERIALIZED VIEW Statement for Data Lake Relational Engine](refresh-materialized-view-statement-for-data-lake-relational-engine-faab95d.md "Initializes or refreshes the data in a materialized view by executing its query definition.")

[DROP MATERIALIZED VIEW Statement for Data Lake Relational Engine](drop-materialized-view-statement-for-data-lake-relational-engine-35de0ef.md "Removes a data type from the database.")

