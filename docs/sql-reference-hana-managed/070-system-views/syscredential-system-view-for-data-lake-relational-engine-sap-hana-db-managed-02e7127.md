<!-- loio02e712750a5844aaa467c394cd9150d8 -->

# SYSCREDENTIAL System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Provides information about credentials for users and components.



<a name="loio02e712750a5844aaa467c394cd9150d8__section_ugr_lhc_fzb"/>

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

object\_id

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

A unique identifier for the credential.

</td>
</tr>
<tr>
<td valign="top">

user\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The user the credential belongs to. NULL for all users

</td>
</tr>
<tr>
<td valign="top">

user\_name

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

Displays the name of the user the credential belongs to. NULL for all users

</td>
</tr>
<tr>
<td valign="top">

component

</td>
<td valign="top">

VARCHAR\( 256 \)

</td>
<td valign="top">

Displays the name of the component the credential is valid for.

</td>
</tr>
<tr>
<td valign="top">

purpose

</td>
<td valign="top">

VARCHAR\( 256 \)

</td>
<td valign="top">

Displays the name or purpose of the credential. e.g. 'SAPHDLRELOADUNLOAD'

</td>
</tr>
<tr>
<td valign="top">

credential\_type

</td>
<td valign="top">

VARCHAR\( 64 \)

</td>
<td valign="top">

Displays the type of the credential. e.g. 'X509'

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

Displays the name of the PSE

</td>
</tr>
</table>



<a name="loio02e712750a5844aaa467c394cd9150d8__section_qtq_d3c_fzb"/>

## Additional Information

The privileges of the current user determine the records displayed.

At a minimum, all credentials owned by the current user are displayed.

