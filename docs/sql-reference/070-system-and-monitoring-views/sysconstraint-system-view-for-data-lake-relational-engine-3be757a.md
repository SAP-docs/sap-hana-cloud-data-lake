<!-- loio3be757ac6c5f1014ace0e4235b05fb2d -->

# SYSCONSTRAINT System View for Data Lake Relational Engine

Each row in the SYS.SYSCONSTRAINT system view describes a named constraint in the database. The underlying system table for this view is ISYSCONSTRAINT.



<a name="loio3be757ac6c5f1014ace0e4235b05fb2d__section_bg3_c2q_b4b"/>

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

constraint\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The unique ID for the constraint.

</td>
</tr>
<tr>
<td valign="top">

constraint\_type

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

The type of constraint:


<dl>
<dt><b>

C

</b></dt>
<dd>

column check constraint



</dd><dt><b>

T

</b></dt>
<dd>

table constraint



</dd><dt><b>

P

</b></dt>
<dd>

primary key



</dd><dt><b>

F

</b></dt>
<dd>

foreign key



</dd><dt><b>

U

</b></dt>
<dd>

unique constraint



</dd>
</dl>



</td>
</tr>
<tr>
<td valign="top">

ref\_object\_id

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

The object ID of the column, table, or index to which the constraint applies.

</td>
</tr>
<tr>
<td valign="top">

table\_object\_id

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

The object ID of the table to which the constraint applies.

</td>
</tr>
<tr>
<td valign="top">

constraint\_name

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

The name of the constraint.

</td>
</tr>
</table>

**Related Information**  


[SYSCONSTRAINT System View for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/7f6192e6d8db4a6da37fb888e0afcd62.html "Each row in the SYS.SYSCONSTRAINT system view describes a named constraint in the database. The underlying system table for this view is ISYSCONSTRAINT.") :arrow_upper_right:

