<!-- loio3beb2d206c5f1014967ef84ffbb10968 -->

# SYSUSERTYPE System View for Data Lake Relational Engine

Each row in the SYS.SYSUSERTYPE system view holds a description of a user-defined data type.



<a name="loio3beb2d206c5f1014967ef84ffbb10968__section_vwg_vhq_b4b"/>

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

type\_id

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

A unique identifying number for the user-defined data type.

</td>
</tr>
<tr>
<td valign="top">

creator

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The user number of the owner of the data type.

</td>
</tr>
<tr>
<td valign="top">

domain\_id

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

The data type on which this user-defined data type is based, indicated by a data type number listed in the SYS.SYSDOMAIN system view.

</td>
</tr>
<tr>
<td valign="top">

nulls

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

Whether the user-defined data type allows nulls. Possible values are Y, N, or U. A value of U indicates that nullability is unspecified.

</td>
</tr>
<tr>
<td valign="top">

width

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

The length of a string column, the precision of a numeric column, or the number of bytes of storage for any other data type.

</td>
</tr>
<tr>
<td valign="top">

scale

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

The number of digits after the decimal point for numeric data type columns, and zero for all other data types.

</td>
</tr>
<tr>
<td valign="top">

type\_name

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

The name for the data type.

</td>
</tr>
<tr>
<td valign="top">

"default"

</td>
<td valign="top">

LONG VARCHAR

</td>
<td valign="top">

The default value for the data type.

</td>
</tr>
<tr>
<td valign="top">

"check"

</td>
<td valign="top">

LONG VARCHAR

</td>
<td valign="top">

The CHECK condition for the data type.

</td>
</tr>
<tr>
<td valign="top">

base\_type\_str

</td>
<td valign="top">

VARCHAR\(32767\)

</td>
<td valign="top">

The annotated type string representing the physical type of the user type.

</td>
</tr>
</table>

**Related Information**  


[SYSUSERTYPE System View for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/164b9020b45548209db5cb851a82589d.html "Each row in the SYS.SYSUSERTYPE system view holds a description of a user-defined data type.") :arrow_upper_right:

