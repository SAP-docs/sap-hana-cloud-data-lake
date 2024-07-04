<!-- loio1c2e04fba3b943e2b6ae23522aad5b5c -->

# SYSPARTITIONS System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Presents group information from the `ISYSPARTITIONS` system table in a readable format



## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system view can be used when connected as follows:

-   Connected to SAP HANA database as a SAP HANA database user, and using SAP HANA database REMOTE\_EXECUTE\_QUERY.





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

table\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The object ID of the table to which the index corresponds.

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

partition\_dbspace\_id

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Object ID of the dbspace where the partition is located.

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

Contains the upper bound for this range partition.

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

Ordinal number of partition.

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

Name of partition

</td>
</tr>
</table>



<a name="loio1c2e04fba3b943e2b6ae23522aad5b5c__section_ar2_nrj_wrb"/>

## Remarks

Each row in the `SYSPARTITIONS` view describes a partitioned object \(table or index\) in the database. The underlying system table for this view is ISYSPARTITIONS.

```
ALTER VIEW "SYS"."SYSPARTITIONS"
  as select * from SYS.ISYSPARTITIONS;
```



<a name="loio1c2e04fba3b943e2b6ae23522aad5b5c__section_egr_nrj_wrb"/>

## Constraints on Underlying System Table

```
primary key (partitioned_object_id, partition_id);
```

```
foreign key (partitioned_object_id) references SYS.ISYSOBJECT;
```

```
foreign key (partition_object_id) references SYS.ISYSOBJECT;
```



<a name="loio1c2e04fba3b943e2b6ae23522aad5b5c__section_gj1_wy1_4yb"/>

## Privileges

To use SAP HANA database REMOTE\_EXECUTE\_QUERY requires the REMOTE EXECUTE privilege on the remote source <hana\_relational\_container\_schema\>\_SOURCE.

-   See [REMOTE\_EXECUTE\_QUERY Usage Examples for Viewing System Views](https://help.sap.com/docs/SAP_HANA_DATA_LAKE/a898e08b84f21015969fa437e89860c8/ada51c0074354a5f99b60c14cffb653c.html).

**Related Information**  


[SYSPARTITIONS System View for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a87f12ff84f210158071ec615c24a7c0.html "Presents group information from the ISYSPARTITIONS system table in a readable format") :arrow_upper_right:

