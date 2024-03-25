<!-- loioa36fd876b1164cdb8100fe41c2b8fd61 -->

# SYSIQTAB System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Presents group information from `ISYSIQTAB` in a readable format. Each row in the SYSIQTAB view describes an IQ table.



## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system view can be used when connected as follows:

-   Connected to SAP HANA database as a SAP HANA database user, and using SAP HANA database REMOTE\_EXECUTE\_QUERY.




> ### Note:  
> This view replaces the deprecated system view SYSIQTABLE.


<table>
<tr>
<th valign="top" rowspan="1">

Column Name

</th>
<th valign="top" rowspan="1">

Column Type

</th>
<th valign="top" rowspan="1">

Description

</th>
</tr>
<tr>
<td valign="top" rowspan="1">

table\_id

</td>
<td valign="top" rowspan="1">

UNSIGNED INT

</td>
<td valign="top" rowspan="1">

Each table is assigned a unique number \(the table number\) that is the primary key.

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

block\_map

</td>
<td valign="top" rowspan="1">

HS\_BLOCKMAPIDENTITY

</td>
<td valign="top" rowspan="1">

For internal use.

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

block\_map\_size

</td>
<td valign="top" rowspan="1">

UNSIGNED INT

</td>
<td valign="top" rowspan="1">

For internal use.

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

vdo

</td>
<td valign="top" rowspan="1">

HS\_VDOIDENTITY

</td>
<td valign="top" rowspan="1">

For internal use.

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

vdoid\_size

</td>
<td valign="top" rowspan="1">

UNSIGNED INT

</td>
<td valign="top" rowspan="1">

For internal use.

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

info\_location

</td>
<td valign="top" rowspan="1">

hs\_vdorecid

</td>
<td valign="top" rowspan="1">

Not used. Always zero.

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

info\_recid\_size

</td>
<td valign="top" rowspan="1">

UNSIGNED INT

</td>
<td valign="top" rowspan="1">

Not used. Always zero.

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

info\_location\_size

</td>
<td valign="top" rowspan="1">

UNSIGNED INT

</td>
<td valign="top" rowspan="1">

Not used. Always zero.

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

commit\_txn\_id

</td>
<td valign="top" rowspan="1">

UNSIGNED BIGINT

</td>
<td valign="top" rowspan="1">

For internal use.

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

txn\_id

</td>
<td valign="top" rowspan="1">

UNSIGNED BIGINT

</td>
<td valign="top" rowspan="1">

For internal use.

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

update\_time

</td>
<td valign="top" rowspan="1">

TIMESTAMP

</td>
<td valign="top" rowspan="1">

Last date and time the IQ table was modified.

</td>
</tr>
<tr>
<td valign="top">

affinity\_map

</td>
<td valign="top">

LONG BINARY

</td>
<td valign="top">

Affinity map ID.

</td>
</tr>
<tr>
<td valign="top">

affinity\_map\_size

</td>
<td valign="top" rowspan="1">

UNSIGNED INT

</td>
<td valign="top">

Size of the affinity map.

</td>
</tr>
</table>



<a name="loioa36fd876b1164cdb8100fe41c2b8fd61__section_krt_4tj_wrb"/>

## Remarks

```
ALTER VIEW "SYS"."SYSIQTAB"
as select * from SYS.ISYSIQTAB;
```



<a name="loioa36fd876b1164cdb8100fe41c2b8fd61__section_i2w_ptj_wrb"/>

## Constraints on Underlying System Table

```
Primary key (table_id);
```



<a name="loioa36fd876b1164cdb8100fe41c2b8fd61__section_gj1_wy1_4yb"/>

## Privileges

To use SAP HANA database REMOTE\_EXECUTE\_QUERY requires the REMOTE EXECUTE privilege on the remote source <hana\_relational\_container\_schema\>\_SOURCE.

-   See [REMOTE\_EXECUTE\_QUERY Usage Examples for Viewing System Views](https://help.sap.com/docs/SAP_HANA_DATA_LAKE/a898e08b84f21015969fa437e89860c8/ada51c0074354a5f99b60c14cffb653c.html).

**Related Information**  


[SYSIQTAB System View for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a5d13c7c84f21015b250b3f01079ca24.html "Presents group information from ISYSIQTAB in a readable format. Each row in the SYSIQTAB view describes an IQ table.") :arrow_upper_right:

