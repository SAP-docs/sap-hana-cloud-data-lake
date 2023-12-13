<!-- loio3be8e1416c5f1014aa0185d6ff33803a -->

# SYSIDXCOL System View for Data Lake Relational Engine

Each row in the SYSIDXCOL system view describes one column of an index described in the SYSIDX system view. The underlying system table for this view is ISYSIDXCOL.



<a name="loio3be8e1416c5f1014aa0185d6ff33803a__section_ijq_wv3_g4b"/>

## Usage

This data lake Relational Engine system view can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




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

**Related Information**  


[SYSIDXCOL System View for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/c788126885234b62a755b24da7d314e9.html "Each row in the SYSIDXCOL system view describes one column of an index described in the SYSIDX system view. The underlying system table for this view is ISYSIDXCOL.") :arrow_upper_right:

