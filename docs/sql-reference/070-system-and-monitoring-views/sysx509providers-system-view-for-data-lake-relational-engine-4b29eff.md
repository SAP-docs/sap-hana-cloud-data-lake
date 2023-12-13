<!-- loio4b29eff9985c4f9cbc9604a54b2feeab -->

# SYSX509PROVIDERS System View for Data Lake Relational Engine

The SYSX509PROVIDERS system view contains a list all of the X.509 providers configured in the database.



<a name="loio4b29eff9985c4f9cbc9604a54b2feeab__section_vwg_vhq_b4b"/>

## Usage

This data lake Relational Engine system view can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




<table>
<tr>
<th valign="top">

Column Name

</th>
<th valign="top">

Data Type

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

A unique identifier for the X.509 provider.

</td>
</tr>
<tr>
<td valign="top">

x509\_provider\_name

</td>
<td valign="top">

VARCHAR\(256\)

</td>
<td valign="top">

The name of the X.509 provider.

</td>
</tr>
<tr>
<td valign="top">

issuer\_name

</td>
<td valign="top">

VARCHAR\(2048\)

</td>
<td valign="top">

The issuer name of the X.509 provider.

</td>
</tr>
</table>

