<!-- loio817f97c16ce21014ba1dcdaaf046de69 -->

# TRUNCATE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Deletes all rows from a materialized view without deleting the table definition.



## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected to SAP HANA database as a SAP HANA database user..



```
MATERIALIZED VIEW [ <schema-name>.]<materialized-view-name>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio817f97c16ce21014ba1dcdaaf046de69__section_ssv_xzy_wwb"/>

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



<a name="loio817f97c16ce21014ba1dcdaaf046de69__section_zzs_rzy_wwb"/>

## Remarks



### 

The TRUNCATE statement deletes all rows from the materialized view.



<a name="loio817f97c16ce21014ba1dcdaaf046de69__section_lp5_pt4_45b"/>

## Side Effects

-   When you truncate a materialized view, you change the status of the view to uninitialized.

-   A COMMIT is performed before and after a TRUNCATE statement is executed.




<a name="loio817f97c16ce21014ba1dcdaaf046de69__section_a4d_5t4_45b"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – supported by SAP Adaptive Server Enterprise

**Related Information**  


[ALTER MATERIALIZED VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](alter-materialized-view-statement-for-data-lake-relational-engine-sap-hana-db-managed-8169459.md "Alters a materialized view.")

[CREATE MATERIALIZED VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-materialized-view-statement-for-data-lake-relational-engine-sap-hana-db-managed-816c0ee.md "Creates a materialized view.")

[REFRESH MATERIALIZED VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](refresh-materialized-view-statement-for-data-lake-relational-engine-sap-hana-db-managed-817277b.md "Initializes or refreshes the data in a materialized view by executing its query definition.")

[DROP MATERIALIZED VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](drop-materialized-view-statement-for-data-lake-relational-engine-sap-hana-db-managed-50e7633.md "Removes a data type from the database.")

[TRUNCATE Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a627e60884f21015aecdf8c062900097.html "Deletes all rows from a table or materialized view without deleting the table definition.") :arrow_upper_right:

