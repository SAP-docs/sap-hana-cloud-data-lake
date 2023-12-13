<!-- loio71d583fb3d54406198b0392610af4841 -->

# SYSPSECERTIFICATE System View for Data Lake Relational Engine

Provides information about certificates associated with a PSE.



<a name="loio71d583fb3d54406198b0392610af4841__section_v1w_qbq_b4b"/>

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

object\_id

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

Displays a unique identifier for the PSE certificate.

</td>
</tr>
<tr>
<td valign="top">

pse\_id

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

Displays the unique identifier for the PSE

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

certificate\_id

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

Displays the unique ID of the certificate.

</td>
</tr>
<tr>
<td valign="top">

certificate\_name

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

Displays the unique name of the certificate.

</td>
</tr>
<tr>
<td valign="top">

update\_time

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the local date and time of the last create or replace.

</td>
</tr>
<tr>
<td valign="top">

update\_time\_utc

</td>
<td valign="top">

TIMESTAMP WITH TIME ZONE

</td>
<td valign="top">

Displays the UTC date and time of the last create or replace

</td>
</tr>
<tr>
<td valign="top">

certificate\_usage

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

Displays the certificate usage. Valid values are:

-   1: OWN
-   2:CHAIN
-   3: TRUST



</td>
</tr>
<tr>
<td valign="top">

certificate\_usage\_str

</td>
<td valign="top">

VARCHAR\(5\)

</td>
<td valign="top">

Displays the certificate usage name.

</td>
</tr>
<tr>
<td valign="top">

subject\_distinguished\_name

</td>
<td valign="top">

VARCHAR\(2048\)

</td>
<td valign="top">

Displays the distinguished name of the X.509 certificate subject.

</td>
</tr>
<tr>
<td valign="top">

issuer\_distinguished\_name

</td>
<td valign="top">

VARCHAR\(2048\)

</td>
<td valign="top">

Displays the distinguished name of the X.509 certificate issuer.

</td>
</tr>
<tr>
<td valign="top">

valid\_from

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the start time of certificate's validity.

</td>
</tr>
<tr>
<td valign="top">

valid\_until

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the end time of certificate's validity.

</td>
</tr>
</table>



<a name="loio71d583fb3d54406198b0392610af4841__SYSPSECERTIFICATE_additional1"/>

## Additional Information

The privileges of the current user determine the records displayed.

At a minimum, all certificates that reference PSEs owned by the current user are displayed.

If the current user has the MANAGE TRUST system privilege, then all certificates referencing PSEs owned by any user are displayed.

