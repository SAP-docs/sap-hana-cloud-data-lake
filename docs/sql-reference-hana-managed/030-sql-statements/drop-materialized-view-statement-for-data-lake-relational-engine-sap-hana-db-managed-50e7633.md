<!-- loio50e76331a4664b5bb2c4454e80b5f8f4 -->

# DROP MATERIALIZED VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Removes a data type from the database.



<a name="loio50e76331a4664b5bb2c4454e80b5f8f4__section_fyr_c3p_m5b"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected to SAP HANA database as a SAP HANA database user..



```
DROP MATERIALIZED VIEW [ IF EXISTS ] [ <schema-name>.]<mat-view-name>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio50e76331a4664b5bb2c4454e80b5f8f4__section_nhz_wkk_dzb"/>

## Parameters


<dl>
<dt><b>

IF EXISTS

</b></dt>
<dd>

Use if you do not want an error returned when the DROP statement attempts to remove a database object that does not exist.



</dd>
</dl>



<a name="loio50e76331a4664b5bb2c4454e80b5f8f4__section_wsp_xkk_dzb"/>

## Remarks

DROP removes the definition of the indicated database structure.

You cannot execute a DROP MATERIALIZED VIEW statement on an object that is currently being used by another connection.

Executing a DROP MATERIALIZED VIEW statement changes the status of all dependent regular views to INVALID. To determine view dependencies before dropping a materialized view, use the sa\_dependent\_views system procedure.



<a name="loio50e76331a4664b5bb2c4454e80b5f8f4__section_evh_ykk_dzb"/>

## Privileges



### 


<dl>
<dt><b>

Connected to SAP HANA database as a SAP HANA database user.:

</b></dt>
<dd>

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the SAP HANA database REMOTE\_EXECUTE procedure associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).

-   See [REMOTE\_EXECUTE Guidance and Examples for Executing SQL Statements](remote-execute-guidance-and-examples-for-executing-sql-statements-fd99ac0.md).




</dd>
</dl>



<a name="loio50e76331a4664b5bb2c4454e80b5f8f4__section_gq1_zkk_dzb"/>

## Side Effects

-   Automatic commit. Clears the Data window in dbisql.



<a name="loio50e76331a4664b5bb2c4454e80b5f8f4__section_zrs_zkk_dzb"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – supported by SAP Adaptive Server Enterprise



<a name="loio50e76331a4664b5bb2c4454e80b5f8f4__section_nqh_blk_dzb"/>

## Examples

This example drops the materialized view mymatview1 if it exists:

```
DROP IF EXISTS MATERIALIZD VIEW mymatview1;
```

**Related Information**  


[CREATE MATERIALIZED VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-materialized-view-statement-for-data-lake-relational-engine-sap-hana-db-managed-816c0ee.md "Creates a materialized view.")

[ALTER MATERIALIZED VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](alter-materialized-view-statement-for-data-lake-relational-engine-sap-hana-db-managed-8169459.md "Alters a materialized view.")

[DROP MATERIALIZED VIEW Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/35de0ef70fde42bfb4c5c4b311cf8c69.html "Removes a data type from the database.") :arrow_upper_right:

