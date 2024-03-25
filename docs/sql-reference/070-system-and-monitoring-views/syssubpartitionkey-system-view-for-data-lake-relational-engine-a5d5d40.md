<!-- loioa5d5d40e84f2101581f6a7a7c5027bbf -->

# SYSSUBPARTITIONKEY System View for Data Lake Relational Engine

Presents group information from the `ISYSSUBPARTITIONKEY` system table in a readable format.



<a name="loioa5d5d40e84f2101581f6a7a7c5027bbf__section_vwg_vhq_b4b"/>

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

partitioned\_object\_id

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

Unique number assigned to each partitioned object \(table or index\).

</td>
</tr>
<tr>
<td valign="top">

column\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

Identifies which column of the table as part of the partitioning key, Together, partitioned\_object\_id and column\_id identify one column described in the SYSTABCOL system view.

</td>
</tr>
<tr>
<td valign="top">

position

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Position of the column in the partitioning key. A value of 0 indicates the 1st column in the partitioning key. A value of 1 indicates the 2nd column in the partitioning key.

</td>
</tr>
</table>



<a name="loioa5d5d40e84f2101581f6a7a7c5027bbf__SYSSUBPARTITIONKEY_remarks1"/>

## Remarks

The SYSSUBPARTITIONKEY system view contains one row for each column of a partition described in ISYSPARTITION view in a partitioned table described in the ISYSPARTITIONSCHEME view.



<a name="loioa5d5d40e84f2101581f6a7a7c5027bbf__SYSSUBPARTITIONKEY_constraints1"/>

## Constraints on Underlying System Table

```
Primary key (partitioned_object_id, column_id);
```

```
Foreign Key (partitioned_object_id) references SYS.ISYSOBJECT;
```

**Related Information**  


[SYSSUBPARTITIONKEY System View for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/2f22651a93ca4950bf80048c3907a3af.html "Presents group information from the ISYSSUBPARTITIONKEY system table in a readable format.") :arrow_upper_right:

