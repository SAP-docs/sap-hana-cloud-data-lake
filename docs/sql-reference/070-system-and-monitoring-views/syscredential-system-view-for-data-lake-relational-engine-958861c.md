<!-- loio958861c8cb8d4feca312f85ef83be2ed -->

# SYSCREDENTIAL System View for Data Lake Relational Engine

Provides information about credentials for users and components.



<a name="loio958861c8cb8d4feca312f85ef83be2ed__section_v1w_qbq_b4b"/>

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



<a name="loio958861c8cb8d4feca312f85ef83be2ed__SYSCREDENTIAL_addit1"/>

## Additional Information

The privileges of the current user determine the records displayed.

At a minimum, all credentials owned by the current user are displayed.

If the current user has the MANAGE CREDENTIAL system privilege, then all credentials owned by other users are displayed.

