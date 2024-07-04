<!-- loio70e155b239d843ad931a10abffaab86c -->

# SYSDATABASEVARIABLE System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Each row in the SYSDATABASEVARIABLE system view describes one database-scope variable in the database. The underlying system table for this view is ISYSDATABASEVARIABLE.



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



<a name="loio70e155b239d843ad931a10abffaab86c__section_ulg_44j_wrb"/>

## Remarks

Updates to database-scope variable values, for example using the SET statement, do not persist after a database restart. Also, updated values are not reflected in this view; only the initial/default value is visible in this view.



<a name="loio70e155b239d843ad931a10abffaab86c__section_gj1_wy1_4yb"/>

## Privileges

To use SAP HANA database REMOTE\_EXECUTE\_QUERY requires the REMOTE EXECUTE privilege on the remote source <hana\_relational\_container\_schema\>\_SOURCE.

-   See [REMOTE\_EXECUTE\_QUERY Usage Examples for Viewing System Views](https://help.sap.com/docs/SAP_HANA_DATA_LAKE/a898e08b84f21015969fa437e89860c8/ada51c0074354a5f99b60c14cffb653c.html).

**Related Information**  


[SYSDATABASEVARIABLE System View for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/4e5f2244dbb9401592a7e6346198afa0.html "Each row in the SYSDATABASEVARIABLE system view describes one database-scope variable in the database. The underlying system table for this view is ISYSDATABASEVARIABLE.") :arrow_upper_right:

