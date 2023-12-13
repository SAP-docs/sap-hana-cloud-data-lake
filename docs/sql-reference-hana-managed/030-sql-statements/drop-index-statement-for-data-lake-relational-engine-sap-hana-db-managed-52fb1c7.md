<!-- loio52fb1c748541447ebde630204fada322 -->

# DROP INDEX Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Removes an index from the database.



<a name="loio52fb1c748541447ebde630204fada322__section_fyr_c3p_m5b"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected to SAP HANA database as a SAP HANA database user and using the SAP HANA database REMOTE\_EXECUTE procedure.



```
DROP INDEX [ IF EXISTS ] [ <schema-name>.]<table-name>.]<index-name>;
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio52fb1c748541447ebde630204fada322__section_uhs_rtj_dzb"/>

## Parameters


<dl>
<dt><b>

IF EXISTS

</b></dt>
<dd>

Use if you do not want an error returned when the DROP statement attempts to remove a database object that does not exist.



</dd>
</dl>



<a name="loio52fb1c748541447ebde630204fada322__section_zsj_stj_dzb"/>

## Remarks

DROP INDEX deletes any explicitly created index. It deletes an implicitly created index only if there are no unique or foreign-key constraints or associated primary key.

DROP INDEX is prevented whenever the statement affects a table that is currently being used by another connection.

For a nonunique HG index, DROP INDEX fails if an associated unenforced foreign key exists.

> ### Caution:  



<a name="loio52fb1c748541447ebde630204fada322__section_t2d_ttj_dzb"/>

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

See [GRANT System Privilege Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a3dfcb0284f21015b74ac3cded42ee69.html "Grants specific system privileges to users or roles, with or without administrative rights.") :arrow_upper_right: or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a3e154f084f21015996d891a5e9d33d2.html "Grants database object-level privileges on individual objects and schemas to a user or role.") :arrow_upper_right: for assistance with granting privileges.



<a name="loio52fb1c748541447ebde630204fada322__section_fm1_5tj_dzb"/>

## Side Effects

-   Do not delete views owned by the DBO user. Deleting such views orAutomatic commit. Clears the Data window in dbisql. DROP INDEX close all cursors for the current connection.
-   Local temporary tables are an exception; no commit is performed when one is dropped.



<a name="loio52fb1c748541447ebde630204fada322__section_gmb_f5j_dzb"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – supported by SAP Adaptive Server Enterprise



<a name="loio52fb1c748541447ebde630204fada322__section_mrv_f5j_dzb"/>

## Examples

This example drops an index named myindex1:

```
DROP INDEX myindex1;
```

**Related Information**  


[CREATE INDEX Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-index-statement-for-data-lake-relational-engine-sap-hana-db-managed-afc9ba6.md "Creates an index on a specified table, or pair of tables. Once an index is created, it is never referenced in a SQL statement again except to delete it using the DROP INDEX statement.")

[ALTER INDEX Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](alter-index-statement-for-data-lake-relational-engine-sap-hana-db-managed-daf745a.md "Renames indexes in base or global temporary tables, foreign key role names of indexes and foreign keys explicitly created by a user, or changes the clustered nature of an index on a catalog store table. You can't rename indexes created to enforce key constraints.")

[DROP INDEX Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/82d6c17a134e4837865c91016a2847c4.html "Removes an index from the database.") :arrow_upper_right:

