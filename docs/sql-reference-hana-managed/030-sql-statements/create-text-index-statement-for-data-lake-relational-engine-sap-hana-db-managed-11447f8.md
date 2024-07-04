<!-- loio11447f8825504a4b8cc578f3204aec12 -->

# CREATE TEXT INDEX Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Creates a TEXT index and specifies the text configuration object to use.



<a name="loio11447f8825504a4b8cc578f3204aec12__section_wnl_ffg_s1c"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected to SAP HANA database as a SAP HANA database user..



```
CREATE TEXT INDEX <text-index-name>
   ON [ { <owner> | <schema-name> }]<table-name>( <column-name>,
   [ CONFIGURATION [ <owner>]<text-configuration-name>]
   [ IMMEDIATE REFRESH ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



## Parameters


<dl>
<dt><b>

ON

</b></dt>
<dd>

Specifies the table and column on which to build the TEXT index.



</dd><dt><b>

CONFIGURATION

</b></dt>
<dd>

Specifies the text configuration object to use when creating the TEXT index. If this clause is not specified, the default\_char text configuration object is used.



</dd><dt><b>

IMMEDIATE REFRESH

</b></dt>
<dd>

\(Default\) refreshes the TEXT index each time changes in the underlying table impact data in the TEXT index. Only permitted value for tables in data lake Relational Engine main store. Once created, the IMMEDIATE REFRESH clause cannot be changed.



</dd>
</dl>



## Remarks

You cannot create a TEXT index on views or temporary tables, or on an IN SYSTEM materialized view. The BEGIN PARALLEL IQ…END PARALLEL IQ statement does not support CREATE TEXT INDEX.



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



## Side Effects

Automatic commit



<a name="loio11447f8825504a4b8cc578f3204aec12__section_ikq_bzc_ybc"/>

## Examples

The following example creates a TEXT index, `myTxtIdx`, on the `CompanyName` column of the `Customers` table:

```
CREATE TEXT INDEX myTxtIdx ON Customers (CompanyName );
```

**Related Information**  


[ALTER TEXT INDEX Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](alter-text-index-statement-for-data-lake-relational-engine-sap-hana-db-managed-979f1f1.md "Renames, moves or alters the definition of a TEXT index.")

[DROP TEXT INDEX for Data Lake Relational Engine \(SAP HANA DB-Managed\)](drop-text-index-for-data-lake-relational-engine-sap-hana-db-managed-986e405.md "Removes a TEXT index from the database.")

[CREATE TEXT INDEX Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a602ced184f210158c90b4b833754412.html "Creates a TEXT index and specifies the text configuration object to use.") :arrow_upper_right:

