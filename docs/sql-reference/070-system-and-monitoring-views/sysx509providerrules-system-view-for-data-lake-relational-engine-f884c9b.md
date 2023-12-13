<!-- loiof884c9b98d38433aa0a3ed0b7a586d1d -->

# SYSX509PROVIDERRULES System View for Data Lake Relational Engine

The SYSX509PROVIDERRULES system view contains all of the matching rules for X.509 providers.



<a name="loiof884c9b98d38433aa0a3ed0b7a586d1d__section_vwg_vhq_b4b"/>

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

x509\_provider\_id

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

A unique identifier for the X.509 provider.

</td>
</tr>
<tr>
<td valign="top">

position

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

The order of the rule \(1-based indexing\).

</td>
</tr>
<tr>
<td valign="top">

matching\_rule

</td>
<td valign="top">

VARCHAR\(2048\)

</td>
<td valign="top">

The matching rule for the subject distinguished name.

</td>
</tr>
</table>

