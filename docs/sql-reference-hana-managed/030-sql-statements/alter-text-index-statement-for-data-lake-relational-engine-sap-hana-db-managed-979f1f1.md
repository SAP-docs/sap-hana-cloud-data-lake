<!-- loio979f1f112e474dd0bc116ae2ded88f35 -->

# ALTER TEXT INDEX Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Renames, moves or alters the definition of a TEXT index.



<a name="loio979f1f112e474dd0bc116ae2ded88f35__section_dks_21d_ybc"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected to SAP HANA database as a SAP HANA database user..



```
ALTER TEXT INDEX [ { <owner> | <schema-name> }.]<text-index-name>
   ON [ { <owner> | <schema-name> }.]<table-name>  
   RENAME { AS | TO } <new-name>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio979f1f112e474dd0bc116ae2ded88f35__section_zrz_fbd_ybc"/>

## Parameters


<dl>
<dt><b>

RENAME

</b></dt>
<dd>

Renames the TEXT index.



</dd>
</dl>



<a name="loio979f1f112e474dd0bc116ae2ded88f35__section_ezq_gbd_ybc"/>

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



<a name="loio979f1f112e474dd0bc116ae2ded88f35__section_uqn_rdd_ybc"/>

## Side Effects

Automatic commit



<a name="loio979f1f112e474dd0bc116ae2ded88f35__section_zhf_sdd_ybc"/>

## Examples

The following example creates a TEXT index, `MyTextIndex`, defining it as IMMEDIATE REFRESH, rename the TEXT index to `Text_index_daily`, and move the TEXT index to a dbspace named `tispace`:

```
CREATE TEXT INDEX MyTextIndex ON Customers ( CompanyName ) IMMEDIATE REFRESH;
ALTER TEXT INDEX MyTextIndex ON Customers RENAME AS Text_index_daily;
ALTER TEXT INDEX Text_Index_Daily ON Customers MOVE TO tispace;
```

**Related Information**  


[CREATE TEXT INDEX Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-text-index-statement-for-data-lake-relational-engine-sap-hana-db-managed-11447f8.md "Creates a TEXT index and specifies the text configuration object to use.")

[DROP TEXT INDEX for Data Lake Relational Engine \(SAP HANA DB-Managed\)](drop-text-index-for-data-lake-relational-engine-sap-hana-db-managed-986e405.md "Removes a TEXT index from the database.")

[ALTER TEXT INDEX Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a602711784f21015955aed036a843754.html "Renames, moves or alters the definition of a TEXT index.") :arrow_upper_right:

