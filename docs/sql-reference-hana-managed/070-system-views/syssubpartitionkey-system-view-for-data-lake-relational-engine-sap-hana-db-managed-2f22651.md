<!-- loio2f22651a93ca4950bf80048c3907a3af -->

# SYSSUBPARTITIONKEY System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Presents group information from the `ISYSSUBPARTITIONKEY` system table in a readable format.



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



<a name="loio2f22651a93ca4950bf80048c3907a3af__section_wf2_hdf_xrb"/>

## Remarks

The SYSSUBPARTITIONKEY system view contains one row for each column of a partition described in ISYSPARTITION view in a partitioned table described in the ISYSPARTITIONSCHEME view.



<a name="loio2f22651a93ca4950bf80048c3907a3af__section_czr_hdf_xrb"/>

## Constraints on Underlying System Table

```
Primary key (partitioned_object_id, column_id);
```

```
Foreign Key (partitioned_object_id) references SYS.ISYSOBJECT;
```



<a name="loio2f22651a93ca4950bf80048c3907a3af__section_gj1_wy1_4yb"/>

## Privileges

To use SAP HANA database REMOTE\_EXECUTE\_QUERY requires the REMOTE EXECUTE privilege on the remote source <hana\_relational\_container\_schema\>\_SOURCE.

-   See [REMOTE\_EXECUTE\_QUERY Usage Examples for Viewing System Views](https://help.sap.com/docs/SAP_HANA_DATA_LAKE/a898e08b84f21015969fa437e89860c8/ada51c0074354a5f99b60c14cffb653c.html).

**Related Information**  


[SYSSUBPARTITIONKEY System View for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a5d5d40e84f2101581f6a7a7c5027bbf.html "Presents group information from the ISYSSUBPARTITIONKEY system table in a readable format.") :arrow_upper_right:

