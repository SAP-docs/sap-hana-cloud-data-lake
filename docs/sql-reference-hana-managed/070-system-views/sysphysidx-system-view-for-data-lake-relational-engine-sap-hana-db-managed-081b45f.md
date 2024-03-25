<!-- loio081b45f1908b4c548c200032f5d7123f -->

# SYSPHYSIDX System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Each row in the SYSPHYSIDX system view defines a physical index in the database. The underlying system table for this view is ISYSPHYSIDX.



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

The object ID of the table to which the index corresponds.

</td>
</tr>
<tr>
<td valign="top">

phys\_index\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The unique number of the physical index within its table.

</td>
</tr>
<tr>
<td valign="top">

root

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Identifies the location of the root page of the physical index in the database file.

</td>
</tr>
<tr>
<td valign="top">

key\_value\_count

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The number of distinct key values in the index.

</td>
</tr>
<tr>
<td valign="top">

leaf\_page\_count

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The number of leaf index pages.

</td>
</tr>
<tr>
<td valign="top">

depth

</td>
<td valign="top">

UNSIGNED SMALLINT

</td>
<td valign="top">

The depth \(number of levels\) of the physical index.

</td>
</tr>
<tr>
<td valign="top">

max\_key\_distance

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

For system use only.

</td>
</tr>
<tr>
<td valign="top">

seq\_transitions

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

For system use only.

</td>
</tr>
<tr>
<td valign="top">

rand\_transitions

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

For system use only.

</td>
</tr>
<tr>
<td valign="top">

rand\_distance

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

For system use only.

</td>
</tr>
<tr>
<td valign="top">

allocation\_bitmap

</td>
<td valign="top">

LONG VARBIT

</td>
<td valign="top">

For system use only.

</td>
</tr>
<tr>
<td valign="top">

long\_value\_bitmap

</td>
<td valign="top">

LONG VARBIT

</td>
<td valign="top">

For system use only.

</td>
</tr>
</table>



<a name="loio081b45f1908b4c548c200032f5d7123f__section_gj1_wy1_4yb"/>

## Privileges

To use SAP HANA database REMOTE\_EXECUTE\_QUERY requires the REMOTE EXECUTE privilege on the remote source <hana\_relational\_container\_schema\>\_SOURCE.

-   See [REMOTE\_EXECUTE\_QUERY Usage Examples for Viewing System Views](https://help.sap.com/docs/SAP_HANA_DATA_LAKE/a898e08b84f21015969fa437e89860c8/ada51c0074354a5f99b60c14cffb653c.html).

**Related Information**  


[SYSPHYSIDX System View for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/3be96a6e6c5f1014b5218fc23d4599d6.html "Each row in the SYSPHYSIDX system view defines a physical index in the database. The underlying system table for this view is ISYSPHYSIDX.") :arrow_upper_right:

