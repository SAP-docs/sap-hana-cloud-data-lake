<!-- loio991b4fb75bed4696885132f2c32419be -->

# RESERVED\_KEYWORDS Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Turns on individual keywords that are disabled by default.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Setting Database Options](remote-execute-usage-examples-for-setting-database-options-0023bea.md).



<a name="loio991b4fb75bed4696885132f2c32419be__section_jb2_khy_lrb"/>

## Syntax

```
RESERVED_KEYWORDS = <string_expression>
```



<a name="loio991b4fb75bed4696885132f2c32419be__section_ymm_khy_lrb"/>

## Allowed Values

String



<a name="loio991b4fb75bed4696885132f2c32419be__section_w4c_lhy_lrb"/>

## Default

' ' \(the empty string\)



<a name="loio991b4fb75bed4696885132f2c32419be__section_ufx_l5b_dxb"/>

## Privileges

Privilege Category: SYSTEM



### 

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio991b4fb75bed4696885132f2c32419be__section_dvv_4hy_lrb"/>

## Scope

-   Option can be set at the database \(PUBLIC\) level only.

-   Takes effect immediately.




<a name="loio991b4fb75bed4696885132f2c32419be__section_cgk_phy_lrb"/>

## Remarks

This option turns on individual keywords that are disabled by default. Only the LIMIT keyword can be turned on.



<a name="loio991b4fb75bed4696885132f2c32419be__section_lbv_phy_lrb"/>

## Examples

The following statement allows the LIMIT keyword to be recognized as a keyword:

```
SET OPTION RESERVED_KEYWORDS = 'LIMIT';
```

You cannot turn on the keywords SET, OPTION, and OPTIONS. The following determine whether a word is identified as a keyword \(in order of precedence\):

-   It appears in the SAP SQL Anywhere list of reserved words
-   It is turned on with the RESERVED\_KEYWORDS option
-   It is turned off with the NON\_KEYWORDS option

Each setting of this option replaces the previous setting. The following statement clears all previous settings:

```
SET OPTION RESERVED_KEYWORDS = ;
```

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[Reserved Words in Data Lake Relational Engine \(SAP HANA DB-Managed\)](../010-sql-language-elements/reserved-words-in-data-lake-relational-engine-sap-hana-db-managed-2bbe71e.md "Some keywords in SQL are also reserved words.")

[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine database behaves or performs.") :arrow_upper_right:

[RESERVED_KEYWORDS Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a248737984f21015a82f960e9878cbd1.html "Turns on individual keywords that are disabled by default.") :arrow_upper_right:

