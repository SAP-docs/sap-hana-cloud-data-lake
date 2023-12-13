<!-- loio7f6192e6d8db4a6da37fb888e0afcd62 -->

# SYSCONSTRAINT System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Each row in the SYS.SYSCONSTRAINT system view describes a named constraint in the database. The underlying system table for this view is ISYSCONSTRAINT.



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



<a name="loio7f6192e6d8db4a6da37fb888e0afcd62__section_gj1_wy1_4yb"/>

## Privileges

To use SAP HANA database REMOTE\_EXECUTE\_QUERY requires the REMOTE EXECUTE privilege on the remote source <hana\_relational\_container\_schema\>\_SOURCE.

-   See [REMOTE\_EXECUTE\_QUERY Usage Examples for Viewing System Views](https://help.sap.com/docs/SAP_HANA_DATA_LAKE/a898e08b84f21015969fa437e89860c8/ada51c0074354a5f99b60c14cffb653c.html).

**Related Information**  


[SYSCONSTRAINT System View for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/3be757ac6c5f1014ace0e4235b05fb2d.html "Each row in the SYS.SYSCONSTRAINT system view describes a named constraint in the database. The underlying system table for this view is ISYSCONSTRAINT.") :arrow_upper_right:

