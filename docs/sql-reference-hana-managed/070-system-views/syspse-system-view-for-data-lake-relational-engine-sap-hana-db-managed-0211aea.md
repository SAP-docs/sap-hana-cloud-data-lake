<!-- loio0211aea22f614e758ca420afb7ac5175 -->

# SYSPSE System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Provides information about personal security environments \(PSE\).



<a name="loio0211aea22f614e758ca420afb7ac5175__section_svw_lhc_fzb"/>

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

pse\_id

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

Displays a unique identifier for the PSE.

</td>
</tr>
<tr>
<td valign="top">

pse\_name

</td>
<td valign="top">

VARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the PSE.

</td>
</tr>
<tr>
<td valign="top">

owner

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

Displays user\_id of PSE owner

</td>
</tr>
<tr>
<td valign="top">

owner\_name

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

Displays the owner of the PSE.

</td>
</tr>
</table>



<a name="loio0211aea22f614e758ca420afb7ac5175__section_kp1_lpc_fzb"/>

## Additional Information

The privileges of the current user determine the records displayed.

At a minimum, all PSEs owned by the current user are displayed.

