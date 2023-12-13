<!-- loioa3db32e184f21015827dfb364642c1a6 -->

# SYSLDAPSERVER System View for Data Lake Relational Engine

Presents information on the `ISYSLDAPSERVER` system table in a readable format.



<a name="loioa3db32e184f21015827dfb364642c1a6__section_v1w_qbq_b4b"/>

## Usage

This data lake Relational Engine system view can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



The ISYSLDAPSERVER system table defines a set of attributes for the LDAP server.


<table>
<tr>
<th valign="top">

Column Name

</th>
<th valign="top">

Column Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

ldsrv\_id

</td>
<td valign="top">

UNSIGNED BIGINT NOT NULL

</td>
<td valign="top">

A unique identifier for the LDAP server that is the primary keyand is used by the login policy to refer to the LDAP server.

</td>
</tr>
<tr>
<td valign="top">

ldsrv\_name

</td>
<td valign="top">

CHAR\(128\) NOT NULL

</td>
<td valign="top">

The name assigned to the LDAP server.

</td>
</tr>
<tr>
<td valign="top">

ldsrv\_state

</td>
<td valign="top">

CHAR\(9\) NOT NULL

</td>
<td valign="top">

Read-only state of the LDAP server:

-   1 – RESET
-   2 – READY
-   3 – ACTIVE
-   4 – FAILED
-   5 – SUSPENDED

> ### Note:  
> A numeric value is stored in system table; a corresponding text value appears in the system view.



</td>
</tr>
<tr>
<td valign="top">

ldsrv\_start\_tls

</td>
<td valign="top">

TINYINT NOT NULL

</td>
<td valign="top">

Controls whether Transport Layer Security \(TLS\) is used to connect to the LDAP server. This provides encrypted communication for connections and searches with the LDAP server in conjunction with TRUSTED\_CERTIFCATE\_FILE.

Valid range:

-   1 – ON
-   0 – OFF \(default\)



</td>
</tr>
<tr>
<td valign="top">

ldsrv\_num\_retries

</td>
<td valign="top">

TINYINT NOT NULL

</td>
<td valign="top">

Controls the number of authenticate attempts allowed with the LDAP server before returning a failure or initiating a failover \(if specified\).

Valid range: 1–60

Default value: 3

</td>
</tr>
<tr>
<td valign="top">

ldsrv\_timeout

</td>
<td valign="top">

UNSIGNED INT NOT NULL

</td>
<td valign="top">

Controls the timeout value \(in milliseconds\) for connections or searches.

Valid range: 1–3600000 \(1 hour\)

Default value: 10000

</td>
</tr>
<tr>
<td valign="top">

ldsrv\_last\_state\_change

</td>
<td valign="top">

TIMESTAMP NOT NULL

</td>
<td valign="top">

Indicates the time the last state change occurred. The value is stored in Coordinated Universal Time \(UTC\), regardless of the local time zone of the LDAP server.

</td>
</tr>
<tr>
<td valign="top">

ldsrv\_search\_url

</td>
<td valign="top">

CHAR\(1024\) NULL

</td>
<td valign="top">

The LDAP URL to be used to find the Distinguished Name \(DN\) for a user based on their user ID.

</td>
</tr>
<tr>
<td valign="top">

ldsrv\_auth\_url

</td>
<td valign="top">

CHAR\(1024\) NULL

</td>
<td valign="top">

The LDAP search string to be used to find the DN for a user given their user ID.

</td>
</tr>
<tr>
<td valign="top">

ldsrv\_access\_dn

</td>
<td valign="top">

CHAR\(1024\) NULL

</td>
<td valign="top">

The DN used to access the LDAP server for searches to obtain the DN for a user ID.

</td>
</tr>
<tr>
<td valign="top">

ldsrv\_access\_dn\_pwd

</td>
<td valign="top">

VARBINARY\(1024\) NULL

</td>
<td valign="top">

The password for the access account. The password is symmetrically encrypted when stored on disk.

</td>
</tr>
</table>

