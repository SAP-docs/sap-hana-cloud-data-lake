<!-- loio80ec5b7639274fb58a0d680ef35009b6 -->

# SYSPROCPARM System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Each row in the SYSPROCPARM system view describes one parameter, result set column, or return value of a procedure or function in the database. The underlying system table for this view is ISYSPROCPARM.



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

proc\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

Uniquely identifies the procedure or function to which the parameter belongs.

</td>
</tr>
<tr>
<td valign="top">

parm\_id

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Each procedure starts numbering parameters at 1. The order of parameter numbers corresponds to the order in which they were defined. For functions, the first parameter has the name of the function and represents the return value for the function.

</td>
</tr>
<tr>
<td valign="top">

parm\_type

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

The type of parameter is one of the following:


<dl>
<dt><b>

0

</b></dt>
<dd>

Normal parameter \(variable\)



</dd><dt><b>

1

</b></dt>
<dd>

Result column - used with a procedure that returns result sets



</dd><dt><b>

2

</b></dt>
<dd>

SQLSTATE error value



</dd><dt><b>

3

</b></dt>
<dd>

SQLCODE error value



</dd><dt><b>

4

</b></dt>
<dd>

Return value from function



</dd>
</dl>



</td>
</tr>
<tr>
<td valign="top">

parm\_mode\_in

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

Indicates whether the parameter supplies a value to the procedure or function \(IN or INOUT parameters\).

</td>
</tr>
<tr>
<td valign="top">

parm\_mode\_out

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

Indicates whether the parameter returns a value from the procedure or function \(OUT or INOUT parameters\) or columns in the RESULT clause.

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

Identifies the data type for the parameter, by the data type number listed in the SYSDOMAIN system view.

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

Contains the length of a string parameter, the precision of a numeric parameter, or the number of bytes of storage for any other data type.

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

For numeric data types, the number of digits after the decimal point. For all other data types, the value of this column is 1.

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

The user type of the parameter, if applicable.

</td>
</tr>
<tr>
<td valign="top">

parm\_name

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

The name of the parameter.

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

Default value of the parameter. Provided for informational purposes only.

</td>
</tr>
<tr>
<td valign="top">

remarks

</td>
<td valign="top">

LONG VARCHAR

</td>
<td valign="top">

Always returns NULL. Provided to allow the use of previous versions of ODBC drivers with newer personal database servers.

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

The annotated type string representing the physical type of the parameter.

</td>
</tr>
</table>



<a name="loio80ec5b7639274fb58a0d680ef35009b6__section_txc_hpf_xrb"/>

## Remarks

The SYSPROCPARM system view is updated when a procedure or function is created or altered, including using the ALTER PROCEDURE...RECOMPILE statement.

Additionally, SYSPROCPARM is updated whenever a checkpoint is run if the out-of-date procedure or function meets the following conditions:

-   The procedure or function has been referenced since it was altered.
-   The procedure either has a RESULT clause or is not a recursive procedure with calls nested ten deep to other procedures that do not have RESULT clauses.



<a name="loio80ec5b7639274fb58a0d680ef35009b6__section_gj1_wy1_4yb"/>

## Privileges

To use SAP HANA database REMOTE\_EXECUTE\_QUERY requires the REMOTE EXECUTE privilege on the remote source <hana\_relational\_container\_schema\>\_SOURCE.

-   See [REMOTE\_EXECUTE\_QUERY Usage Examples for Viewing System Views](https://help.sap.com/docs/SAP_HANA_DATA_LAKE/a898e08b84f21015969fa437e89860c8/ada51c0074354a5f99b60c14cffb653c.html).

**Related Information**  


[SYSPROCPARM System View for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/3be984286c5f101483cb9e3f71175aa7.html "Each row in the SYSPROCPARM system view describes one parameter, result set column, or return value of a procedure or function in the database. The underlying system table for this view is ISYSPROCPARM.") :arrow_upper_right:

