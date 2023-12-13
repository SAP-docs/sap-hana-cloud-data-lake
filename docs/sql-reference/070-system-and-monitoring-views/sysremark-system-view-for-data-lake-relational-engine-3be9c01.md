<!-- loio3be9c0156c5f1014b7d8d601763e6946 -->

# SYSREMARK System View for Data Lake Relational Engine

Each row in the SYSREMARK system view describes a remark \(or comment\) for an object. The underlying system table for this view is ISYSREMARK.



<a name="loio3be9c0156c5f1014b7d8d601763e6946__section_vwg_vhq_b4b"/>

## Usage

This data lake Relational Engine system view can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




<table>
<tr>
<th valign="top">

Column

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

object\_id

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

The internal ID for the object that has an associated remark.

</td>
</tr>
<tr>
<td valign="top">

remarks

</td>
<td valign="top">

LONG VARCHAR

</td>
<td valign="top">

The remark or comment associated with the object.

</td>
</tr>
</table>

**Related Information**  


[SYSREMARK System View for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/7b03435105ce4359a93864a0d3feec43.html "Each row in the SYSREMARK system view describes a remark (or comment) for an object. The underlying system table for this view is ISYSREMARK.") :arrow_upper_right:

