<!-- loio34e354059097469d9864ff18b541f343 -->

# TIMESTAMP\_COLUMNS\_AS\_DATETIMEX Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Controls whether DATETIMEX data type columns are automatically created when TIMESTAMPS data type columns are requested.



<a name="loio34e354059097469d9864ff18b541f343__section_fcx_cxv_4bc"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be set when:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user. This option cannot be set when connected to SAP HANA database as a SAP HANA database user.



<a name="loio34e354059097469d9864ff18b541f343__section_zhs_fc3_mrb"/>

## Syntax

```
TIMESTAMP_COLUMNS_AS_DATETIMEX = { ON | OFF };
```



<a name="loio34e354059097469d9864ff18b541f343__section_l1b_gc3_mrb"/>

## Allowed Values

ON, OFF



<a name="loio34e354059097469d9864ff18b541f343__section_tlp_5l3_hwb"/>

## Default

The default value of the TIMESTAMP\_COLUMNS\_AS\_DATETIMEX database option depends on when your data lake Relational Engine instance was created.


<table>
<tr>
<th valign="top">

Default

</th>
<th valign="top">

Configuration

</th>
</tr>
<tr>
<td valign="top">

ON

</td>
<td valign="top">

-   The instance was created using version QRC 2/2023 or later.
-   A new relational container was created after a forced upgrade to version QRC 2/2023 or later.



</td>
</tr>
<tr>
<td valign="top">

OFF

</td>
<td valign="top">

-   The instance was created using a version prior to version QRC 2/2023.



</td>
</tr>
</table>



<a name="loio34e354059097469d9864ff18b541f343__section_pxx_cwc_dxb"/>

## Privileges

Privilege Category: SYSTEM



### 

> ### Restriction:  
> This option can only be set when directly connected as the HDLADMIN user.



<a name="loio34e354059097469d9864ff18b541f343__section_nd4_hc3_mrb"/>

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

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
</tr>
</table>



## Remarks

When enabled, specifying a TIMESTAMP data type during execution of the CREATE and ALTER TABLE statements substitutes any columns specified in the statement with a TIMESTAMP data type with the DATETIMEX data type. This setting affects columns in IQ base and global/local temporary tables created by CREATE TABLE, ALTER TABLE, or DECLARE LOCAL TEMPORARY TABLE statements.

To determine the current value for the option, execute the following statement:

```
SELECT connection_property('Timestamp_Columns_as_datetimex');
```

The default can be manually changed by executing:

```
SET OPTION PUBLIC.TIMESTAMP_COLUMNS_AS_DATETIMEX = { ON | OFF };
```

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[SET\_TEMPORARY\_OPTION Procedure for SAP HANA Database](../080-sap-hana-database-for-data-lake-relational-engine/set-temporary-option-procedure-for-sap-hana-database-abcd703.md "Grant database options temporarily for the current connection only on a data lake Relational Engine relational container.")

[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2024_3_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine instance behaves or performs.") :arrow_upper_right:

[TIMESTAMP Data Type Precision in Data Lake Relational Engine \(SAP HANA DB-Managed\)](../020-sql-data-types/timestamp-data-type-precision-in-data-lake-relational-engine-sap-hana-db-managed-5cbca14.md "Precision conflicts between TIMESTAMP data types result in data loss.")

[TIMESTAMP_COLUMNS_AS_DATETIMEX Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/082fdf9f04bc43acbc014a0842c43ea9.html "Controls whether DATETIMEX data type columns are automatically created when TIMESTAMPS data type columns are requested.") :arrow_upper_right:

