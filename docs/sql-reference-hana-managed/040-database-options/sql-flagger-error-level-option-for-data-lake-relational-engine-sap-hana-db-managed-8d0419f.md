<!-- loio8d0419f947274ddfb7c2be8bb35ac237 -->

# SQL\_FLAGGER\_ERROR\_LEVEL Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Controls the behavior in response to any SQL code that is not part of the specified standard.



<a name="loio8d0419f947274ddfb7c2be8bb35ac237__section_dzz_4jj_kyb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be set when:

-   Connected to SAP HANA database as a SAP HANA database user..
-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio8d0419f947274ddfb7c2be8bb35ac237__section_pzf_ctz_lrb"/>

## Syntax

```
SQL_FLAGGER_ERROR_LEVEL = <string_expression>
```



<a name="loio8d0419f947274ddfb7c2be8bb35ac237__section_drp_ctz_lrb"/>

## Allowed Values

-   OFF
-   SQL:1992/EntrySQL:1992/Intermediate
-   SQL:1992/Full
-   SQL:1999/Core
-   SQL:1999/Package
-   SQL:2003/Core
-   SQL:2003/Package



<a name="loio8d0419f947274ddfb7c2be8bb35ac237__section_bbd_dtz_lrb"/>

## Default

OFF



<a name="loio8d0419f947274ddfb7c2be8bb35ac237__section_l21_y5b_dxb"/>

## Privileges

Privilege Category: PUBLIC



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

-   Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



</dd>
</dl>



<a name="loio8d0419f947274ddfb7c2be8bb35ac237__section_j4s_dtz_lrb"/>

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

Yes

</td>
<td valign="top">

Yes

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

Yes \(current connection only\)

</td>
<td valign="top">

No

</td>
</tr>
</table>



<a name="loio8d0419f947274ddfb7c2be8bb35ac237__section_gqb_3tz_lrb"/>

## Remarks

Flags as an error any SQL code that is not part of a specified standard. For example, specifying SQL:2003/Package causes the database server to flag syntax that is not full SQL/2003 syntax.

For compatibility with previous data lake Relational Engine versions, the following values are also accepted, and are mapped as specified. Compatibility values for SQL\_FLAGGER\_ERROR\_LEVEL are:

-   E – flag syntax that is not entry-level SQL92 syntax. Corresponds to SQL:1992/Entry.
-   I – flag syntax that is not intermediate-level SQL92 syntax. Corresponds to SQL:1992/Intermediate.
-   F – flag syntax that is not full-SQL92 syntax. Corresponds to SQL:1992/Full.
-   W – allow all supported syntax. Corresponds to OFF.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[SET\_TEMPORARY\_OPTION Procedure for SAP HANA Database](../080-sap-hana-database-for-data-lake-relational-engine/set-temporary-option-procedure-for-sap-hana-database-abcd703.md "Grant database options temporarily for the current connection only on a data lake Relational Engine relational container.")

[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2024_1_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine instance behaves or performs.") :arrow_upper_right:

[SQL_FLAGGER_ERROR_LEVEL Option \[TSQL\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a6561a9684f21015b8c7dfeda2c69941.html "Controls the behavior in response to any SQL code that is not part of the specified standard.") :arrow_upper_right:

