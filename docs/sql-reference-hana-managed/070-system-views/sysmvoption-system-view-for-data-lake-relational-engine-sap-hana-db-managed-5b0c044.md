<!-- loio5b0c044c69034850a8d3006feb79ce7f -->

# SYSMVOPTION System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Each row in the SYSMVOPTION system view describes the setting of one option value for a materialized viewor text index at the time of its creation. The name of the option can be found in the SYSMVOPTIONNAME system view. The underlying system table for this view is ISYSMVOPTION.



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

view\_object\_id

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

The object ID of the materialized view.

</td>
</tr>
<tr>
<td valign="top">

option\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

A unique number identifying the option in the database. To see the option name, see the SYSMVOPTIONNAME system view.

</td>
</tr>
<tr>
<td valign="top">

option\_value

</td>
<td valign="top">

LONG VARCHAR

</td>
<td valign="top">

The value of the option when the materialized view was created.

</td>
</tr>
</table>



<a name="loio5b0c044c69034850a8d3006feb79ce7f__section_gj1_wy1_4yb"/>

## Privileges

To use SAP HANA database REMOTE\_EXECUTE\_QUERY requires the REMOTE EXECUTE privilege on the remote source <hana\_relational\_container\_schema\>\_SOURCE.

-   See [REMOTE\_EXECUTE\_QUERY Usage Examples for Viewing System Views](https://help.sap.com/docs/SAP_HANA_DATA_LAKE/a898e08b84f21015969fa437e89860c8/ada51c0074354a5f99b60c14cffb653c.html).

**Related Information**  


[SYSMVOPTION System View for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/3be939606c5f1014a581c83fbbc9b790.html "Each row in the SYSMVOPTION system view describes the setting of one option value for a materialized view or text index at the time of its creation. The name of the option can be found in the SYSMVOPTIONNAME system view. The underlying system table for this view is ISYSMVOPTION.") :arrow_upper_right:

