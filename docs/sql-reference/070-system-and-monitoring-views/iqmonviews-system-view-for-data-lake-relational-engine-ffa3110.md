<!-- loioffa31103c3f34e769feb586b1dc9481b -->

# iqmonViews System View for Data Lake Relational Engine

An online help view providing a list of all available data lake Relational Engine monitoring views.



<a name="loioffa31103c3f34e769feb586b1dc9481b__section_v1w_qbq_b4b"/>

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

The unique identifier of the data lake Relational Engine monitoring view.

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

The name of the data lake Relational Engine monitoring view.

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

The description of the monitoring view. For example: ***Provides information about the threads used by the IQ thread manager.***

</td>
</tr>
</table>



<a name="loioffa31103c3f34e769feb586b1dc9481b__section_ahv_5mg_bfb"/>

## Usage

Use the iqmonViews monitoring view to display a list of all available data lake Relational Engine monitoring views which you can use to monitor data lake Relational Engine system health.

Execute this command:

```
select * from iqmonViews;
```

The monitoring views listed by iqmonViews can help you troubleshoot common data lake Relational Engine performance problems. For diagnostic use-case information, see the [SAP HANA Cloud, Data Lake Performance and Tuning for Data Lake Relational Engine (Monitoring Views)](https://help.sap.com/viewer/028be133f34c4d2d998c6fbc258659c5/2024_3_QRC/en-US/56032dd760ca4790a55d069d4475b441.html "This document shows you how to use the monitoring views to monitor data lake Relational Engine system health, and to help you troubleshoot performance issues.") :arrow_upper_right: manual.



<a name="loioffa31103c3f34e769feb586b1dc9481b__section_kpt_vmz_1fb"/>

## Privileges

You must have the MONITOR system privilege to access this view. DBAs can consult [Granting and Revoking a System Privilege from Users and Roles](https://help.sap.com/viewer/a89a0a8384f21015b1e7adbeca456f73/2024_3_QRC/en-US/a43bcb8284f210158039b1793a92a4fc.html "Grant and revoke a specific system privilege to and from specific users or roles, with or without administrative rights.") :arrow_upper_right: and [Alphabetical List of System Privileges for Data Lake Relational Engine](../080-sql-statements/alphabetical-list-of-system-privileges-for-data-lake-relational-engine-a449325.md) for information on granting the MONITOR system privilege to a user.

