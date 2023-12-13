<!-- loio3be952c66c5f10148f4c9702f0c7742d -->

# SYSOPTION System View for Data Lake Relational Engine

The SYSOPTION system view contains the options one row for each option setting stored in the database.



<a name="loio3be952c66c5f10148f4c9702f0c7742d__section_v1w_qbq_b4b"/>

## Usage

This data lake Relational Engine system view can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



Each user can have their own setting for a given option. In addition, settings for the PUBLIC role define the default settings to be used for users that do not have their own setting. The underlying system table for this view is ISYSOPTION.


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

user\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The user number to whom the option setting applies.

</td>
</tr>
<tr>
<td valign="top">

"option"

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

The name of the option.

</td>
</tr>
<tr>
<td valign="top">

setting

</td>
<td valign="top">

LONG VARCHAR

</td>
<td valign="top">

The current setting for the option.

</td>
</tr>
</table>

