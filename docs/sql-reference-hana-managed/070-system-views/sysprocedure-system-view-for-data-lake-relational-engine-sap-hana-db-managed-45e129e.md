<!-- loio45e129efea3d4e8daa6fa4df8090d56c -->

# SYSPROCEDURE System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Each row in the SYSPROCEDURE system view describes one procedure in the database. The underlying system table for this view is ISYSPROCEDURE.



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

The internal procedure number for the procedure, uniquely identifying it in the database.

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

The owner of the procedure.

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

The internal ID for the procedure, uniquely identifying it in the database.

</td>
</tr>
<tr>
<td valign="top">

proc\_name

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

The name of the procedure. One creator cannot have two procedures with the same name.

</td>
</tr>
<tr>
<td valign="top">

proc\_defn

</td>
<td valign="top">

LONG VARCHAR

</td>
<td valign="top">

The definition of the procedure after it has been parsed and unparsed by the database server

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

Remarks about the procedure. This value is stored in the ISYSREMARK system table.

</td>
</tr>
<tr>
<td valign="top">

replicate

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

Internal use only.

</td>
</tr>
<tr>
<td valign="top">

srvid

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

If the procedure is a proxy for a procedure on a remote database server, then this value indicates the remote server.

</td>
</tr>
<tr>
<td valign="top">

source

</td>
<td valign="top">

LONG VARCHAR

</td>
<td valign="top">

The preserved source for the procedure. This value is stored in the ISYSSOURCE system table. Content is only stored in this column when the preserve\_source\_format option is set to On.

</td>
</tr>
<tr>
<td valign="top">

avg\_num\_rows

</td>
<td valign="top">

FLOAT

</td>
<td valign="top">

Information collected for use in query optimization when the procedure appears in the FROM clause.

</td>
</tr>
<tr>
<td valign="top">

avg\_cost

</td>
<td valign="top">

FLOAT

</td>
<td valign="top">

Information collected for use in query optimization when the procedure appears in the FROM clause.

</td>
</tr>
<tr>
<td valign="top">

stats

</td>
<td valign="top">

LONG BINARY

</td>
<td valign="top">

Information collected for use in query optimization when the procedure appears in the FROM clause.

</td>
</tr>
<tr>
<td valign="top">

dialect

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

Returns W for Watcom SQL procedures and functions, and T for Transact SQL procedures and functions.

</td>
</tr>
<tr>
<td valign="top">

is\_deterministic

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

Returns NULL for procedures. Returns Y if a function is marked as deterministic, N if it is marked as not deterministic, and U if it is not marked either way.

</td>
</tr>
<tr>
<td valign="top">

is\_external

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

Returns Y if the function is external and N if it is not.

</td>
</tr>
<tr>
<td valign="top">

external\_language

</td>
<td valign="top">

VARCHAR\(128\)

</td>
<td valign="top">

Returns NULL if the procedure is not external and 'native' if the procedure uses the original interface. Otherwise, it contains the language of the procedure.

</td>
</tr>
<tr>
<td valign="top">

external\_name

</td>
<td valign="top">

VARCHAR\(32767\)

</td>
<td valign="top">

Returns NULL if the procedure is not external. Otherwise, it contains the external name of the procedure.

</td>
</tr>
<tr>
<td valign="top">

sql\_security

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

Returns I if the procedure is SQL SECURITY INVOKER and D if the procedure is SQL SECURITY DEFINER.

</td>
</tr>
</table>



<a name="loio45e129efea3d4e8daa6fa4df8090d56c__section_gj1_wy1_4yb"/>

## Privileges

To use SAP HANA database REMOTE\_EXECUTE\_QUERY requires the REMOTE EXECUTE privilege on the remote source <hana\_relational\_container\_schema\>\_SOURCE.

-   See [REMOTE\_EXECUTE\_QUERY Usage Examples for Viewing System Views](https://help.sap.com/docs/SAP_HANA_DATA_LAKE/a898e08b84f21015969fa437e89860c8/ada51c0074354a5f99b60c14cffb653c.html).

**Related Information**  


[SYSPROCEDURE System View for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/3be97af56c5f1014a1b1a537360ec408.html "Each row in the SYSPROCEDURE system view describes one procedure in the database. The underlying system table for this view is ISYSPROCEDURE.") :arrow_upper_right:

