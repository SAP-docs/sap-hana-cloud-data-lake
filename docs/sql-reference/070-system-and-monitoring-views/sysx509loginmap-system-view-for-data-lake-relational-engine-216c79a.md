<!-- loio216c79ae42e64b938908d96238bcccb8 -->

# SYSX509LOGINMAP System View for Data Lake Relational Engine

The SYSX509LOGINMAP system view lists the X509 certificate-to-user mappings configured in the data lake Relational Engine database.



<a name="loio216c79ae42e64b938908d96238bcccb8__section_vwg_vhq_b4b"/>

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

UNSIGNED BIGINT NOT NULL

</td>
<td valign="top">

A unique identifier for the mapping between each subject distinguished name.

</td>
</tr>
<tr>
<td valign="top">

database\_uid

</td>
<td valign="top">

UNSIGNED INT NOT NULL

</td>
<td valign="top">

The database user ID to which the subject distinguished name is mapped.

</td>
</tr>
<tr>
<td valign="top">

subject\_name

</td>
<td valign="top">

VARCGAR\(2048\) NUL

</td>
<td valign="top">

The subject of the X.509 certificate of the user. If the user is mapped with a wildcard \(ANY\) for this subject, the value is NULL.

</td>
</tr>
<tr>
<td valign="top">

x509\_provider\_id

</td>
<td valign="top">

UNSIGNED BIGINT NOT NULL

</td>
<td valign="top">

The object ID of the X.509 provider.

</td>
</tr>
</table>

