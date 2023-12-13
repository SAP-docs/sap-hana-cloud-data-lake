<!-- loio4e5f2244dbb9401592a7e6346198afa0 -->

# SYSDATABASEVARIABLE System View for Data Lake Relational Engine

Each row in the SYSDATABASEVARIABLE system view describes one database-scope variable in the database. The underlying system table for this view is ISYSDATABASEVARIABLE.



<a name="loio4e5f2244dbb9401592a7e6346198afa0__section_bg3_c2q_b4b"/>

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

variable\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The ID of the database variable.

</td>
</tr>
<tr>
<td valign="top">

object\_id

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

The internal ID for the database-scope variable, uniquely identifying it in the database.

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

The owner of the database variable.

</td>
</tr>
<tr>
<td valign="top">

variable\_name

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

The name of the database variable.

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

The ID of the data type as listed in the SYSDOMAIN system view.

</td>
</tr>
<tr>
<td valign="top">

width

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The length of a string the database variable can hold, the precision of numeric values for the column, or the number of bytes of storage needed for any other data type.

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

The number of digits after the decimal point for NUMERIC or DECIMAL data type variables. For a database variable containing a string, a value of 1 indicates character-length semantics and 0 indicates byte-length semantics.

</td>
</tr>
<tr>
<td valign="top">

user\_type

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

The data type of the database variable, or NULL if no type value is present.

</td>
</tr>
<tr>
<td valign="top">

initial\_value

</td>
<td valign="top">

LONG BINARY

</td>
<td valign="top">

The initial value of the database variable. If no value is specified, NULL is used.

If the initial value was set using an expression, the expression is evaluated at creation time and the resulting constant is stored in this column \(not the expression\).

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

The annotated type string representing the physical type of the database variable.

</td>
</tr>
<tr>
<td valign="top">

initial\_value\_string

</td>
<td valign="top">

LONG VARCHAR

</td>
<td valign="top">

The string representation of the initial value of the database variable.

</td>
</tr>
</table>



<a name="loio4e5f2244dbb9401592a7e6346198afa0__SYSDATABASEVARIABLE_remarks1"/>

## Remarks

Updates to database-scope variable values, for example using the SET statement, do not persist after a database restart. Also, updated values are not reflected in this view; only the initial/default value is visible in this view.

**Related Information**  


[SYSDATABASEVARIABLE System View for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/70e155b239d843ad931a10abffaab86c.html "Each row in the SYSDATABASEVARIABLE system view describes one database-scope variable in the database. The underlying system table for this view is ISYSDATABASEVARIABLE.") :arrow_upper_right:

