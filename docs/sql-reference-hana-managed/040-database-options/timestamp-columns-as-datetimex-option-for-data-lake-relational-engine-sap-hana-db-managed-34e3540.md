<!-- loio34e354059097469d9864ff18b541f343 -->

# TIMESTAMP\_COLUMNS\_AS\_DATETIMEX Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Controls whether DATETIMEX data type columns are automatically created when TIMESTAMPS data type columns are requested.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio34e354059097469d9864ff18b541f343__section_zhs_fc3_mrb"/>

## Syntax

```
TIMESTAMP_COLUMNS_AS_DATETIMEX = { ON | OFF }
```



<a name="loio34e354059097469d9864ff18b541f343__section_l1b_gc3_mrb"/>

## Allowed Values

ON, OFF



<a name="loio34e354059097469d9864ff18b541f343__section_tlp_5l3_hwb"/>

## Default

OFF



<a name="loio34e354059097469d9864ff18b541f343__section_pxx_cwc_dxb"/>

## Privileges

Privilege Category: PUBLIC



### 

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



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



## Remarks

When enabled, specifying a TIMESTAMP data type during execution of the CREATE and ALTER TABLE statements substitutes any columns specified in the statement with a TIMESTAMP data type with the DATETIMEX data type. This setting affects columns in IQ base and global/local temporary tables created by CREATE TABLE, ALTER TABLE, or DECLARE LOCAL TEMPORARY TABLE statements.

The default can be manually changed by executing:

```
SET OPTION PUBLIC.TIMESTAMP_COLUMNS_AS_DATETIMEX = "{ ON | OFF }";
```

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine database behaves or performs.") :arrow_upper_right:

[Decimal Precision of the TIMESTAMP Data Type in Data Lake Relational Engine \(SAP HANA DB-Managed\)](../020-sql-data-types/decimal-precision-of-the-timestamp-data-type-in-data-lake-relational-engine-sap-hana-db-m-5cbca14.md "Decimal precision for TIMESTAMP data type columns is controlled by the TIMESTAMP_COLUMNS_AS_DATETIMEX database option.")

[TIMESTAMP_COLUMNS_AS_DATETIMEX Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/082fdf9f04bc43acbc014a0842c43ea9.html "Controls whether DATETIMEX data type columns are automatically created when TIMESTAMPS data type columns are requested.") :arrow_upper_right:

