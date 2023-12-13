<!-- loioa34ee8b984f210158899e4685d277754 -->

# SYSCERTIFICATE System View for Data Lake Relational Engine

Each row of the SYSCERTIFICATE system view stores a certificate in text PEM-format.This view includes certificates with and without an associated PSE.



<a name="loioa34ee8b984f210158899e4685d277754__section_i2m_qpq_b4b"/>

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

Displays the ID of the certificate.

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

Displays the user ID of the certificate owner.

</td>
</tr>
<tr>
<td valign="top">

cert\_name

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

Displays the certificate name.

</td>
</tr>
<tr>
<td valign="top">

contents

</td>
<td valign="top">

LONG BINARY

</td>
<td valign="top">

Displays the certificate contents in a compressed form.

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

Displays the UTC date and time of the last create or replace.

</td>
</tr>
<tr>
<td valign="top">

purpose

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

Displays the purpose of the certificate. Valid values are:

-   1 - for JWT
-   2 - for X.509
-   NULL



</td>
</tr>
<tr>
<td valign="top">

jwt\_provider\_id

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

Displays the JWT provider associated with the certificate, or NULL if the purpose is not JWT.

</td>
</tr>
<tr>
<td valign="top">

x509\_provider\_id

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

Displays the X.509 provider associated with the certificate, or NULL if the purpose is not X.509.

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

Displays the start time of certificate's validity

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

Displays the end time of certificate's validity

</td>
</tr>
</table>



<a name="loioa34ee8b984f210158899e4685d277754__SYSCERTIFICATE_constraints1"/>

## Constraints on Underlying System Table

```
PRIMARY KEY (object_id);
```

```
UNIQUE INDEX (cert_name);
```



<a name="loioa34ee8b984f210158899e4685d277754__SYSCERTIFICATE_additional1"/>

## Additional Information

The privileges of the current user determine the records displayed.

At a minimum, all certificates owned by the current user and any certificates associated with a PSE owned by the current user are displayed.

If the current user has the MANAGE TRUST or MANAGE CERTIFICATES system privileges, then certificates owned by other users and certificates associated with a PSE owned by other users are displayed.

