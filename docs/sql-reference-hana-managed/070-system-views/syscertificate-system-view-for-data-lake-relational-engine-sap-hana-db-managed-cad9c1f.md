<!-- loiocad9c1fffb084582a27db15c4d18d315 -->

# SYSCERTIFICATE System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Each row of the SYSCERTIFICATE system view stores a certificate in text PEM-format.This view includes certificates with and without an associated PSE.



<a name="loiocad9c1fffb084582a27db15c4d18d315__section_svw_lhc_fzb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system view can be used when connected as follows:

-   Connected to SAP HANA database as a SAP HANA database user, and using SAP HANA database REMOTE\_EXECUTE\_QUERY.





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



<a name="loiocad9c1fffb084582a27db15c4d18d315__section_pg2_l4c_fzb"/>

## Constraints on Underlying System Table

```
PRIMARY KEY (object_id);
```

```
UNIQUE INDEX (cert_name);
```



<a name="loiocad9c1fffb084582a27db15c4d18d315__section_fqt_l4c_fzb"/>

## Additional Information

The privileges of the current user determine the records displayed.

At a minimum, all certificates owned by the current user and any certificates associated with a PSE owned by the current user are displayed.

