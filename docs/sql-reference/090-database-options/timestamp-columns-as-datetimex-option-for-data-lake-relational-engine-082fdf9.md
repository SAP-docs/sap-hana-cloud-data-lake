<!-- loio082fdf9f04bc43acbc014a0842c43ea9 -->

# TIMESTAMP\_COLUMNS\_AS\_DATETIMEX Option for Data Lake Relational Engine

Controls whether DATETIMEX data type columns are automatically created when TIMESTAMPS data type columns are requested.



<a name="loio082fdf9f04bc43acbc014a0842c43ea9__section_ajq_xqq_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio082fdf9f04bc43acbc014a0842c43ea9__timestamp_columns_datetimex_syntax1"/>

## Syntax

```
TIMESTAMP_COLUMNS_AS_DATETIMEX = { ON | OFF };
```



<a name="loio082fdf9f04bc43acbc014a0842c43ea9__timestamp_columns_datetimex_values1"/>

## Allowed Values

ON, OFF



<a name="loio082fdf9f04bc43acbc014a0842c43ea9__timestamp_columns_datetimex_default1"/>

## Default

The default value of the TIMESTAMP\_COLUMNS\_AS\_DATETIMEX database option depends on when your data lake Relational Engine instance was createdand the mode specified.


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

-   The instance was created using version QRC 2/2023 or laterand using the mode **Configure to be most compatible with SAP HANA database.**.



</td>
</tr>
<tr>
<td valign="top">

OFF

</td>
<td valign="top">

-   The instances was created using version QRC 2/2023 or later and using the mode **Configure to be most compatible with SAP IQ.**.
-   The instance was created using a version prior to version QRC 2/2023regardless of the mode specified.



</td>
</tr>
</table>



<a name="loio082fdf9f04bc43acbc014a0842c43ea9__timestamp_columns_datetimex_priv1"/>

## Privileges

Privilege Category: SYSTEM



### 

Requires the SET ANY CUSTOMER SYSTEM OPTION system privilege to set this database option.



<a name="loio082fdf9f04bc43acbc014a0842c43ea9__timestamp_columns_datetimex_scope1"/>

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



<a name="loio082fdf9f04bc43acbc014a0842c43ea9__timestamp_columns_datetimex_remarks1"/>

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


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[TIMESTAMP_COLUMNS_AS_DATETIMEX Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/34e354059097469d9864ff18b541f343.html "Controls whether DATETIMEX data type columns are automatically created when TIMESTAMPS data type columns are requested.") :arrow_upper_right:

[Date and Time Data Types in Data Lake Relational Engine](../020-sql-data-types/date-and-time-data-types-in-data-lake-relational-engine-a51e8fb.md "Use date and time data types for storing dates and times.")

[Decimal Precision of the TIMESTAMP Data Type in Data Lake Relational Engine](../020-sql-data-types/decimal-precision-of-the-timestamp-data-type-in-data-lake-relational-engine-520ce6c.md "Decimal precision for TIMESTAMP data type columns is controlled by the TIMESTAMP_COLUMNS_AS_DATETIMEX database option.")

