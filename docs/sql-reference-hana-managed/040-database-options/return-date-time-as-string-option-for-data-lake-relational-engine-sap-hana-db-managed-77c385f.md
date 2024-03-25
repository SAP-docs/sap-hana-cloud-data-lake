<!-- loio77c385f40ad1417d8f1ea8ca653456e9 -->

# RETURN\_DATE\_TIME\_AS\_STRING Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Controls how a date, time, or timestamp value is passed to the client application when queried.



<a name="loio77c385f40ad1417d8f1ea8ca653456e9__section_dzz_4jj_kyb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be set when:

-   Connected to SAP HANA database as a SAP HANA database user..
-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio77c385f40ad1417d8f1ea8ca653456e9__section_yj2_nqz_lrb"/>

## Syntax

```
RETURN_DATE_TIME_AS_STRING = { ON | OFF }
```



<a name="loio77c385f40ad1417d8f1ea8ca653456e9__section_jzn_nqz_lrb"/>

## Allowed Values

ON, OFF



<a name="loio77c385f40ad1417d8f1ea8ca653456e9__section_dl3_4qz_lrb"/>

## Default

OFF



<a name="loio77c385f40ad1417d8f1ea8ca653456e9__section_clk_gvb_dxb"/>

## Privileges

Privilege Category: PUBLIC



### 

The privileges required depend on your data lake Relational Engine \(SAP HANA DB-Managed\) connection method:


<dl>
<dt><b>

Connected to SAP HANA database as a SAP HANA database user.:

</b></dt>
<dd>

-   To set a database option temporarily, use the SET\_TEMPORARY\_OPTION procedure, which requires you be a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.

    -   See [SET\_TEMPORARY\_OPTION Procedure for SAP HANA Database](../080-sap-hana-database-for-data-lake-relational-engine/set-temporary-option-procedure-for-sap-hana-database-abcd703.md).





</dd><dt><b>

Connected directly to data lake Relational Engine as a data lake Relational Engine user:

</b></dt>
<dd>

-   Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



</dd>
</dl>



<a name="loio77c385f40ad1417d8f1ea8ca653456e9__section_scf_pqz_lrb"/>

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

No

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

Yes \(current connection only\)

</td>
<td valign="top">

No

</td>
</tr>
</table>



<a name="loio77c385f40ad1417d8f1ea8ca653456e9__section_ikg_qqz_lrb"/>

## Remarks

RETURN\_DATE\_TIME\_AS\_STRING indicates whether date, time, and timestamp values are returned to applications as a date or time data type or as a string.

When this option is set to ON, the server converts the date, time, or timestamp value to a string before it is sent to the client in order to preserve the TIMESTAMP\_FORMAT, DATE\_FORMAT, or TIME\_FORMAT option setting.

Interactive SQL automatically turns the RETURN\_DATE\_TIME\_AS\_STRING option ON.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[DATE\_FORMAT Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](date-format-option-for-data-lake-relational-engine-sap-hana-db-managed-3e2ecb4.md "Sets the format used for dates retrieved from the database.")

[SET\_TEMPORARY\_OPTION Procedure for SAP HANA Database](../080-sap-hana-database-for-data-lake-relational-engine/set-temporary-option-procedure-for-sap-hana-database-abcd703.md "Grant database options temporarily for the current connection only on a data lake Relational Engine relational container.")

[TIME\_FORMAT Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](time-format-option-for-data-lake-relational-engine-sap-hana-db-managed-5f6bdfd.md "Sets the format used for times retrieved from the database.")

[TIMESTAMP\_FORMAT Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](timestamp-format-option-for-data-lake-relational-engine-sap-hana-db-managed-002566c.md "Sets the format used for timestamps retrieved from the database.")

[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2024_1_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine instance behaves or performs.") :arrow_upper_right:

[RETURN_DATE_TIME_AS_STRING Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a652ffd684f2101583dcef31685601cf.html "Controls how a date, time, or timestamp value is passed to the client application when queried.") :arrow_upper_right:

