<!-- loio889aa3fe26d34d678b2c85f99c95bc50 -->

# iqmonViewColumns System View for Data Lake Relational Engine

An online help view providing column names, data types, and column descriptions for the data lake Relational Engine monitoring views.



<a name="loio889aa3fe26d34d678b2c85f99c95bc50__section_skb_fwg_k4b"/>

## Usage

This data lake Relational Engine system view can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.


<table>
<tr>
<th valign="top">

Column Name

</th>
<th valign="top">

Data Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

ViewID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

The unique ID of the monitoring view.

</td>
</tr>
<tr>
<td valign="top">

ViewName

</td>
<td valign="top">

VARCHAR\(64\)

</td>
<td valign="top">

The name of the monitoring view.

</td>
</tr>
<tr>
<td valign="top">

ColumnName

</td>
<td valign="top">

VARCHAR\(64\)

</td>
<td valign="top">

The monitoring view column name.

</td>
</tr>
<tr>
<td valign="top">

ColumnNumber

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

The monitoring view column number.

</td>
</tr>
<tr>
<td valign="top">

DataType

</td>
<td valign="top">

VARCHAR\(25\)

</td>
<td valign="top">

The data type of the monitoring view column.

</td>
</tr>
<tr>
<td valign="top">

Size

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

The size of the monitoring view column.

</td>
</tr>
<tr>
<td valign="top">

Description

</td>
<td valign="top">

VARCHAR\(512\)

</td>
<td valign="top">

The description of the monitoring view column.

</td>
</tr>
</table>



<a name="loio889aa3fe26d34d678b2c85f99c95bc50__section_ixs_cct_kgb"/>

## Usage

Use iqmonViewColumns as online help for the data lake Relational Engine monitoring views.

iqmonViewColumns displays the column names, data types, and column descriptions for all data lake Relational Engine monitoring views. This helps you locate which view — and which columns in those views — contain the system health metrics you're looking for.

To display column data for all monitoring views, use this syntax:

```
select * from iqmonViewColumns;
```

You can limit the focus of iqmonViewColumns to return column information for a particular data lake Relational Engine monitoring view. For example, if you're only interested in the iqmonThreadManager monitoring view columns, use this syntax:

```
select * from iqmonViewColumns where ViewName = iqmonThreadManager;
```

The monitoring view columns listed by iqmonViewColumns can help you troubleshoot common data lake Relational Engine performance problems. For diagnostic use-case information, see the [SAP HANA Cloud, Data Lake Performance and Tuning for Data Lake Relational Engine (Monitoring Views)](https://help.sap.com/viewer/028be133f34c4d2d998c6fbc258659c5/2024_1_QRC/en-US/56032dd760ca4790a55d069d4475b441.html "This document shows you how to use the monitoring views to monitor data lake Relational Engine system health, and to help you troubleshoot performance issues.") :arrow_upper_right: manual.



<a name="loio889aa3fe26d34d678b2c85f99c95bc50__section_kpt_vmz_1fb"/>

## Privileges

You must have the MONITOR system privilege to access this view. DBAs can consult [Granting a System Privilege to a User](https://help.sap.com/viewer/a89a0a8384f21015b1e7adbeca456f73/2024_1_QRC/en-US/a43bcb8284f210158039b1793a92a4fc.html "Allow the granting of specific system privileges to specific users, with or without administrative rights.") :arrow_upper_right: and [Alphabetical List of System Privileges for Data Lake Relational Engine](../080-sql-statements/alphabetical-list-of-system-privileges-for-data-lake-relational-engine-a449325.md) for information on granting the MONITOR system privilege to a user.

