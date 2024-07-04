<!-- loio3be941066c5f1014b6f8dbc61db5c4f3 -->

# SYSMVOPTIONNAME System View for Data Lake Relational Engine

Each row in the SYSMVOPTIONNAME system view gives the name of an option that is stored for each materialized view at the time of its creation. The value for the option can be found in the SYSMVOPTION system view. The underlying system table for this view is ISYSMVOPTIONNAME.



<a name="loio3be941066c5f1014b6f8dbc61db5c4f3__section_vwg_vhq_b4b"/>

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

option\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

A number uniquely identifying the option in the database.

</td>
</tr>
<tr>
<td valign="top">

option\_name

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

The name of the option.

</td>
</tr>
</table>

**Related Information**  


[SYSMVOPTIONNAME System View for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/8c7b66fe90e64870b498bbb2071d3041.html "Each row in the SYSMVOPTIONNAME system view gives the name of an option that is stored for each materialized view at the time of its creation. The value for the option can be found in the SYSMVOPTION system view. The underlying system table for this view is ISYSMVOPTIONNAME.") :arrow_upper_right:

