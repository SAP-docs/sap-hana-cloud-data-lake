<!-- loioc788126885234b62a755b24da7d314e9 -->

# SYSIDXCOL System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Each row in the SYSIDXCOL system view describes one column of an index described in the SYSIDX system view. The underlying system table for this view is ISYSIDXCOL.



## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system view can be used when connected as follows:

-   Connected to SAP HANA database as a SAP HANA database user, and using SAP HANA database REMOTE\_EXECUTE\_QUERY.





<table>
<tr>
<th valign="top">

Column name

</th>
<th valign="top">

Data type

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

Identifies the table to which the index applies.

</td>
</tr>
<tr>
<td valign="top">

index\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

Identifies the index to which the column applies. Together, table\_id and index\_id identify one index described in the SYSIDX system view.

</td>
</tr>
<tr>
<td valign="top">

sequence

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Each column in an index is assigned a unique number starting at 0. The order of these numbers determines the relative significance of the columns in the index. The most important column has sequence number 0.

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

Identifies which column of the table is indexed. Together, table\_id and column\_id identify one column described in the SYSCOLUMN system view.

</td>
</tr>
<tr>
<td valign="top">

"order"

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

Indicates whether the column in the index is kept in ascending\(A\) or descending\(D\) order. This value is NULL for text indexes.

</td>
</tr>
<tr>
<td valign="top">

primary\_column\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The ID of the primary key column that corresponds to this foreign key column. The value is NULL for non foreign key columns.

</td>
</tr>
</table>



<a name="loioc788126885234b62a755b24da7d314e9__section_gj1_wy1_4yb"/>

## Privileges

To use SAP HANA database REMOTE\_EXECUTE\_QUERY requires the REMOTE EXECUTE privilege on the remote source <hana\_relational\_container\_schema\>\_SOURCE.

-   See [REMOTE\_EXECUTE\_QUERY Usage Examples for Viewing System Views](https://help.sap.com/docs/SAP_HANA_DATA_LAKE/a898e08b84f21015969fa437e89860c8/ada51c0074354a5f99b60c14cffb653c.html).

**Related Information**  


[SYSIDXCOL System View for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/3be8e1416c5f1014aa0185d6ff33803a.html "Each row in the SYSIDXCOL system view describes one column of an index described in the SYSIDX system view. The underlying system table for this view is ISYSIDXCOL.") :arrow_upper_right:

