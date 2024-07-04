<!-- loio986e405214dd4c2f9292990694dbfc95 -->

# DROP TEXT INDEX for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Removes a TEXT index from the database.



<a name="loio986e405214dd4c2f9292990694dbfc95__section_wnl_ffg_s1c"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected to SAP HANA database as a SAP HANA database user..



```
DROP TEXT INDEX <text-index-name>
   ON [ { <owner> | <schema-name> }.]<table-name>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio986e405214dd4c2f9292990694dbfc95__section_m5l_rhd_ybc"/>

## Parameters


<dl>
<dt><b>

ON

</b></dt>
<dd>

Specifies the table on which the TEXT index is built.



</dd>
</dl>



<a name="loio986e405214dd4c2f9292990694dbfc95__section_qmd_shd_ybc"/>

## Remarks

You must drop dependent TEXT indexes before you can drop a text configuration object.



<a name="loio986e405214dd4c2f9292990694dbfc95__section_k1w_shd_ybc"/>

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



<a name="loio986e405214dd4c2f9292990694dbfc95__section_phj_b3d_ybc"/>

## Side Effects

Automatic commit



<a name="loio986e405214dd4c2f9292990694dbfc95__section_ccf_c3d_ybc"/>

## Examples

The following example creates and drops the `TextIdx` TEXT index:

```
CREATE TEXT INDEX TextIdx ON Customers ( Street );
DROP TEXT INDEX TextIdx ON Customers;
```

**Related Information**  


[CREATE TEXT INDEX Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-text-index-statement-for-data-lake-relational-engine-sap-hana-db-managed-11447f8.md "Creates a TEXT index and specifies the text configuration object to use.")

[ALTER TEXT INDEX Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](alter-text-index-statement-for-data-lake-relational-engine-sap-hana-db-managed-979f1f1.md "Renames, moves or alters the definition of a TEXT index.")

[DROP TEXT INDEX Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a60331d484f21015b12ac440f67fd4d1.html "Removes a TEXT index from the database.") :arrow_upper_right:

