<!-- loio6dc54aef9f0f46edaea2bbe8c4970ca1 -->

# SYSIQMATERIALIZEDVIEWPINREQUESTS System View in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Displays the mapping of incremental refresh materialized views and all associated pin requests.



<a name="loio6dc54aef9f0f46edaea2bbe8c4970ca1__section_rwn_4nr_gqb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system view can be used when connected as follows:

-   Connected to SAP HANA database as a SAP HANA database user, and using SAP HANA database REMOTE\_EXECUTE\_QUERY.





<table>
<tr>
<th valign="top">

Column Name

</th>
<th valign="top">

Column type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

view\_owner

</td>
<td valign="top">

VARCHAR\(128\)

</td>
<td valign="top">

Displays the owner of the materialized view.

</td>
</tr>
<tr>
<td valign="top">

view\_name

</td>
<td valign="top">

VARCHAR\(128\)

</td>
<td valign="top">

Displays the name of the materialized view.

</td>
</tr>
<tr>
<td valign="top">

pin\_id

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

Displays the ID of the pin request.

</td>
</tr>
</table>



<a name="loio6dc54aef9f0f46edaea2bbe8c4970ca1__section_gj1_wy1_4yb"/>

## Privileges

To use SAP HANA database REMOTE\_EXECUTE\_QUERY requires the REMOTE EXECUTE privilege on the remote source <hana\_relational\_container\_schema\>\_SOURCE.

-   See [REMOTE\_EXECUTE\_QUERY Usage Examples for Viewing System Views](https://help.sap.com/docs/SAP_HANA_DATA_LAKE/a898e08b84f21015969fa437e89860c8/ada51c0074354a5f99b60c14cffb653c.html).

