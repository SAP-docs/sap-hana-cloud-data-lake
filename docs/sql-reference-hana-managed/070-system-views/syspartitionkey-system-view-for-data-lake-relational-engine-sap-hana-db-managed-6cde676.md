<!-- loio6cde676a747347609a0c559e3324e62a -->

# SYSPARTITIONKEY System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Presents group information from `ISYSPARTITIONKEY` in a readable format.



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

Each partitioned object \(table\) is assigned a unique object number.

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

The column ID identifies the table column as part of the partitioning key.

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

Position of this column in the partitioning key. Position is 0 based. A position of 0 indicates the 1st column in the partitioning key.

</td>
</tr>
</table>



<a name="loio6cde676a747347609a0c559e3324e62a__section_wh4_vrj_wrb"/>

## Remarks

Each row in the `SYSPARTITIONKEY` view describes a partitioned object \(table or index\) in the database.

```
ALTER VIEW "SYS"."SYSPARTITIONKEY"
as select * from SYS.ISYSPARTITIONKEY;
```



<a name="loio6cde676a747347609a0c559e3324e62a__section_m1n_wrj_wrb"/>

## Constraints on Underlying System Table

```
Primary key (partitioned_object_id, column_id);
```

```
Foreign key (partitioned_object_id) references SYS.ISYSOBJECT;
```



<a name="loio6cde676a747347609a0c559e3324e62a__section_gj1_wy1_4yb"/>

## Privileges

To use SAP HANA database REMOTE\_EXECUTE\_QUERY requires the REMOTE EXECUTE privilege on the remote source <hana\_relational\_container\_schema\>\_SOURCE.

-   See [REMOTE\_EXECUTE\_QUERY Usage Examples for Viewing System Views](https://help.sap.com/docs/SAP_HANA_DATA_LAKE/a898e08b84f21015969fa437e89860c8/ada51c0074354a5f99b60c14cffb653c.html).

**Related Information**  


[SYSPARTITIONKEY System View for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a5d4d0f884f21015b5589652d668a182.html "Presents group information from ISYSPARTITIONKEY in a readable format.") :arrow_upper_right:

