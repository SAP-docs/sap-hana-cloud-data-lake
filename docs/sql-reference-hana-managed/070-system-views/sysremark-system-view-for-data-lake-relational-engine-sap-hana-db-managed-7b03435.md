<!-- loio7b03435105ce4359a93864a0d3feec43 -->

# SYSREMARK System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Each row in the SYSREMARK system view describes a remark \(or comment\) for an object. The underlying system table for this view is ISYSREMARK.



## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system view can be used when connected as follows:

-   Connected to SAP HANA database as a SAP HANA database user, and using SAP HANA database REMOTE\_EXECUTE\_QUERY.





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



<a name="loio7b03435105ce4359a93864a0d3feec43__section_gj1_wy1_4yb"/>

## Privileges

To use SAP HANA database REMOTE\_EXECUTE\_QUERY requires the REMOTE EXECUTE privilege on the remote source <hana\_relational\_container\_schema\>\_SOURCE.

-   See [REMOTE\_EXECUTE\_QUERY Usage Examples for Viewing System Views](https://help.sap.com/docs/SAP_HANA_DATA_LAKE/a898e08b84f21015969fa437e89860c8/ada51c0074354a5f99b60c14cffb653c.html).

**Related Information**  


[SYSREMARK System View for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/3be9c0156c5f1014b7d8d601763e6946.html "Each row in the SYSREMARK system view describes a remark (or comment) for an object. The underlying system table for this view is ISYSREMARK.") :arrow_upper_right:

