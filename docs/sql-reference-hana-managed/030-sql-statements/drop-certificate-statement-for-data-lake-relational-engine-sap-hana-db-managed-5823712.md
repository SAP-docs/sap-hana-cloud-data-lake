<!-- loio5823712c23734d86b5498688b5a0b0df -->

# DROP CERTIFICATE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Drops a certificate from the database.



<a name="loio5823712c23734d86b5498688b5a0b0df__section_wgg_skf_2zb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected to SAP HANA database as a SAP HANA database user..



```
DROP CERTIFICATE [IF EXISTS ] <certificate-name>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio5823712c23734d86b5498688b5a0b0df__section_ix2_5kf_2zb"/>

## Parameters


<dl>
<dt><b>

IF EXISTS

</b></dt>
<dd>

Use if you do not want an error returned when the DROP statement attempts to remove a database object that does not exist.



</dd>
</dl>



<a name="loio5823712c23734d86b5498688b5a0b0df__section_dnt_5kf_2zb"/>

## Remarks

None



<a name="loio5823712c23734d86b5498688b5a0b0df__section_nv3_vkf_2zb"/>

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



<a name="loio5823712c23734d86b5498688b5a0b0df__section_tyz_vkf_2zb"/>

## Side Effects

-   Automatic commit. Clears the Data window in dbisql.



<a name="loio5823712c23734d86b5498688b5a0b0df__section_mjq_wkf_2zb"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – supported by SAP Adaptive Server Enterprise



<a name="loio5823712c23734d86b5498688b5a0b0df__section_bbf_xkf_2zb"/>

## Examples

This example drops the certificate mycert1:

```
DROP CERTIFICATE mycert1;
```

**Related Information**  


[CREATE CERTIFICATE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-certificate-statement-for-data-lake-relational-engine-sap-hana-db-managed-d827f85.md "Adds or replaces a certificate in the database using the given file or string.")

[DROP CERTIFICATE STATEMENT for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/c22eaf42bb524cc58ef660f84743c934.html "Drops a certificate from the database.") :arrow_upper_right:

