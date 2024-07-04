<!-- loio3c389d94400946ca86449766a70a2877 -->

# DROP VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Removes a view from the database.



<a name="loio3c389d94400946ca86449766a70a2877__section_fyr_c3p_m5b"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected to SAP HANA database as a SAP HANA database user..



```
DROP VIEW [ IF EXISTS ] [ <schema-name>.]<view-name>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio3c389d94400946ca86449766a70a2877__section_uqd_cyj_dzb"/>

## Parameters


<dl>
<dt><b>

IF EXISTS

</b></dt>
<dd>

Use if you do not want an error returned when the DROP statement attempts to remove a database object that does not exist.



</dd>
</dl>



<a name="loio3c389d94400946ca86449766a70a2877__section_ftb_dyj_dzb"/>

## Remarks

DROP removes the definition of the indicated database structure.



<a name="loio3c389d94400946ca86449766a70a2877__section_nz1_2yj_dzb"/>

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



<a name="loio3c389d94400946ca86449766a70a2877__section_bhf_hyj_dzb"/>

## Side Effects

-   Automatic commit. Clears the Data window in dbisql.



<a name="loio3c389d94400946ca86449766a70a2877__section_lcg_3yj_dzb"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – supported by SAP Adaptive Server Enterprise



<a name="loio3c389d94400946ca86449766a70a2877__section_vcc_jyj_dzb"/>

## Examples

This example drops the view myview1 if it exits:

```
DROP IF EXISTS VIEW myview1;
```

**Related Information**  


[CREATE VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-view-statement-for-data-lake-relational-engine-sap-hana-db-managed-4d41128.md "Creates a view on the database. Views are used to give a different perspective on the data even though it is not stored that way.")

[ALTER VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](alter-view-statement-for-data-lake-relational-engine-sap-hana-db-managed-6ef5483.md "Replaces a view definition with a modified version.")

[DROP VIEW Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/10a78b1d3ba748e8a3c096e90207a128.html "Removes a view from the database.") :arrow_upper_right:

