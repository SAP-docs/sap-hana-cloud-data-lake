<!-- loiof6a009a1f8f349d3be269032a24d2cb6 -->

# SYSPARTITION System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Presents group information from `ISYSPARTITION` in a readable format.



## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system view can be used when connected as follows:

-   Connected to SAP HANA database as a SAP HANA database user, and using SAP HANA database REMOTE\_EXECUTE\_QUERY.





<table>
<tr>
<th valign="top">

Column Name

</th>
<th valign="top">

Column Type

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

Unique number assigned to each partitioned object \(table\).

</td>
</tr>
<tr>
<td valign="top">

partition\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

Identifies a partition in a partitioned table.

</td>
</tr>
<tr>
<td valign="top">

partition\_object\_id

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

Each table partition is an object itself and is assigned a unique number from the table object or index object.

</td>
</tr>
<tr>
<td valign="top">

partition\_values

</td>
<td valign="top">

LONG VARCHAR

</td>
<td valign="top">

Contains partitioning criteria for range or list partitioning:

-   For range partitioning, values contain the upper bound for this partition.
-   For list partitioning, values contain list of values separated by ','. Position is the ordinal number of partition.



</td>
</tr>
<tr>
<td valign="top">

position

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

Ordinal number of partition. For ranged partition, for position 2 and above, the partition at \(position-1\) contains its exclusive lower bound.

</td>
</tr>
<tr>
<td valign="top">

partition\_name

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

Name of partition.

</td>
</tr>
</table>



<a name="loiof6a009a1f8f349d3be269032a24d2cb6__section_w5q_2sj_wrb"/>

## Remarks

Each row in the `SYSPARTITION` view describes a partitioned object \(table or index\) in the database. The underlying system table for this view is ISYSPARTITION.



<a name="loiof6a009a1f8f349d3be269032a24d2cb6__section_ag2_fsj_wrb"/>

## Constraints on Underlying System Table

```
Primary key (partitioned_object_id, partition_id);
```

```
Unique (partition_object_id, position);
```

```
Foreign key (partition_object_id) references SYS.ISYSOBJECT;
```

```
Foreign key (partitioned_object_id) references SYS.ISYSOBJECT;
```



<a name="loiof6a009a1f8f349d3be269032a24d2cb6__section_gj1_wy1_4yb"/>

## Privileges

To use SAP HANA database REMOTE\_EXECUTE\_QUERY requires the REMOTE EXECUTE privilege on the remote source <hana\_relational\_container\_schema\>\_SOURCE.

-   See [REMOTE\_EXECUTE\_QUERY Usage Examples for Viewing System Views](https://help.sap.com/docs/SAP_HANA_DATA_LAKE/a898e08b84f21015969fa437e89860c8/ada51c0074354a5f99b60c14cffb653c.html).

**Related Information**  


[SYSPARTITION System View for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a5d44e9984f210159983d6f3d800d5db.html "Presents group information from ISYSPARTITION in a readable format.") :arrow_upper_right:

