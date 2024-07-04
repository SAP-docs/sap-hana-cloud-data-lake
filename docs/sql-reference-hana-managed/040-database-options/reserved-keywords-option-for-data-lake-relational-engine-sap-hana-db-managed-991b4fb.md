<!-- loio991b4fb75bed4696885132f2c32419be -->

# RESERVED\_KEYWORDS Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Turns on individual keywords that are disabled by default.



<a name="loio991b4fb75bed4696885132f2c32419be__section_dzz_4jj_kyb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be set when:

-   Connected to SAP HANA database as a SAP HANA database user.
-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



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

The privileges required depend on your data lake Relational Engine \(SAP HANA DB-Managed\) connection method and whether you are setting the option temporarily or permanently:


<dl>
<dt><b>

Connected to SAP HANA database as a SAP HANA database user:

</b></dt>
<dd>

-   To set a database option permanently, use REMOTE\_EXECUTE.

    Requires one of:

    -   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
    -   EXECUTE permission on the SAP HANA database REMOTE\_EXECUTE procedure associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).

    -   See [REMOTE\_EXECUTE Guidance and Examples for Setting Permanent Database Options](remote-execute-guidance-and-examples-for-setting-permanent-database-options-0023bea.md).


-   To set a database option temporarily, use the SET\_TEMPORARY\_OPTION procedure, which requires you be a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.

    -   See [SET\_TEMPORARY\_OPTION Procedure for SAP HANA Database](../080-sap-hana-database-for-data-lake-relational-engine/set-temporary-option-procedure-for-sap-hana-database-abcd703.md).





</dd><dt><b>

Connected directly to data lake Relational Engine as a data lake Relational Engine user:

</b></dt>
<dd>

-   Requires the SET ANY CUSTOMER SYSTEM OPTION system privilege to set this database option.



</dd>
</dl>



<a name="loio991b4fb75bed4696885132f2c32419be__section_dvv_4hy_lrb"/>

## Scope


<table>
<tr>
<th valign="top">

 

</th>
<th valign="top">

PUBLIC Role

</th>
<th valign="top">

For Current User

</th>
<th valign="top">

For Other Users

</th>
</tr>
<tr>
<td valign="top">

Allowed to set permanently?

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

Allowed to set temporarily?

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
</tr>
</table>



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

-   It appears in the data lake Relational Engine list of reserved words
-   It is turned on with the RESERVED\_KEYWORDS option
-   It is turned off with the NON\_KEYWORDS option

Each setting of this option replaces the previous setting. The following statement clears all previous settings:

```
SET OPTION RESERVED_KEYWORDS = ;
```

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[Reserved Words in Data Lake Relational Engine \(SAP HANA DB-Managed\)](../010-sql-language-elements/reserved-words-in-data-lake-relational-engine-sap-hana-db-managed-2bbe71e.md "Some keywords in SQL are also reserved words.")

[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2024_3_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine instance behaves or performs.") :arrow_upper_right:

[RESERVED_KEYWORDS Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a248737984f21015a82f960e9878cbd1.html "Turns on individual keywords that are disabled by default.") :arrow_upper_right:

