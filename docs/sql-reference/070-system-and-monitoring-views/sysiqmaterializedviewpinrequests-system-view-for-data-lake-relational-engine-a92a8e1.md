<!-- loioa92a8e14af424737acaaf44f4bcd60ae -->

# SYSIQMATERIALIZEDVIEWPINREQUESTS System View for Data Lake Relational Engine

Displays the mapping of incremental refresh materialized views and all associated pin requests.



<a name="loioa92a8e14af424737acaaf44f4bcd60ae__section_v1w_qbq_b4b"/>

## Usage

This data lake Relational Engine system view can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




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

