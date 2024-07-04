<!-- loio3be939606c5f1014a581c83fbbc9b790 -->

# SYSMVOPTION System View for Data Lake Relational Engine

Each row in the SYSMVOPTION system view describes the setting of one option value for a materialized viewor text index at the time of its creation. The name of the option can be found in the SYSMVOPTIONNAME system view. The underlying system table for this view is ISYSMVOPTION.



<a name="loio3be939606c5f1014a581c83fbbc9b790__section_vwg_vhq_b4b"/>

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

**Related Information**  


[SYSMVOPTION System View for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/5b0c044c69034850a8d3006feb79ce7f.html "Each row in the SYSMVOPTION system view describes the setting of one option value for a materialized view or text index at the time of its creation. The name of the option can be found in the SYSMVOPTIONNAME system view. The underlying system table for this view is ISYSMVOPTION.") :arrow_upper_right:

