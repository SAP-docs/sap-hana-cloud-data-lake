<!-- loiodbb08c71f0a34f93b2f28d765e123ed0 -->

# TIMESTAMP\_RTRUNCATION Option for Data Lake Relational Engine

Controls whether INSERT, UPDATE, or CAST operations on TIMESTAMP data type columns fails if loss of precision will result.



<a name="loiodbb08c71f0a34f93b2f28d765e123ed0__section_ajq_xqq_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loiodbb08c71f0a34f93b2f28d765e123ed0__timestamp_rtruncation_syntax1"/>

## Syntax

```
TIMESTAMP_RTRUNCATION = { ON | OFF };
```



<a name="loiodbb08c71f0a34f93b2f28d765e123ed0__timestamp_rtruncation_values1"/>

## Allowed Values

ON, OFF



<a name="loiodbb08c71f0a34f93b2f28d765e123ed0__timestamp_rtruncation_default1"/>

## Default

The default value of the TIMESTAMP\_RTRUNCATION database option depends on when your data lake Relational Engine instance was createdand the mode specified.


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

-   The instance was created using version QRC 1/2024 or later.



</td>
</tr>
<tr>
<td valign="top">

OFF

</td>
<td valign="top">

-   The instance was created using a version prior to version QRC 1/2024.



</td>
</tr>
</table>



<a name="loiodbb08c71f0a34f93b2f28d765e123ed0__timestamp_rtruncation_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loiodbb08c71f0a34f93b2f28d765e123ed0__timestamp_rtruncation_scope1"/>

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



<a name="loiodbb08c71f0a34f93b2f28d765e123ed0__timestamp_rtruncation_remarks1"/>

## Remarks

When enabled, any INSERT, UPDATE, or CAST operation on a timestamp data type column that will result in lost precision fails.

To determine the current value for the option, execute the following statement:

```
SELECT connection_property('Timestamp_rtruncation');
```

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[TIMESTAMP Data Type Precision in Data Lake Relational Engine](../020-sql-data-types/timestamp-data-type-precision-in-data-lake-relational-engine-520ce6c.md "Precision conflicts between TIMESTAMP data types result in data loss.")

[Date and Time Data Types in Data Lake Relational Engine](../020-sql-data-types/date-and-time-data-types-in-data-lake-relational-engine-a51e8fb.md "Use date and time data types for storing dates and times.")

[TIMESTAMP_RTRUNCATION Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/7ea796c77e5047c78acff41829be70aa.html "Controls whether INSERT, UPDATE, or CAST operations on TIMESTAMP data type columns fails if loss of precision will result.") :arrow_upper_right:

