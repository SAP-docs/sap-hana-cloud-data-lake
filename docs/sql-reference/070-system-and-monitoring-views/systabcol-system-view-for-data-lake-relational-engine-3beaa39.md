<!-- loio3beaa3956c5f1014883cb0c3e3559cc9 -->

# SYSTABCOL System View for Data Lake Relational Engine

The SYS.SYSTABCOL system view contains one row for each column of each table and view in the database.



<a name="loio3beaa3956c5f1014883cb0c3e3559cc9__section_v1w_qbq_b4b"/>

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

table\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The object ID of the table or view to which the column belongs.

</td>
</tr>
<tr>
<td valign="top">

column\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The ID of the column. For each table, column numbering starts at 1.

The column\_id value determines the order of columns in the result set when SELECT \* is used. It also determines the column order for an INSERT statement when a list of column names isn’t provided.

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

The data type for the column, indicated by a data type number listed in the SYS.SYSDOMAIN system view.

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

Indicates whether NULL values are allowed in the column.

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

The length of a string column, the precision of numeric columns, or the number of bytes of storage for any other data type. For a string with character-length semantics, width indicates the number of characters.

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

The number of digits after the decimal point for NUMERIC or DECIMAL data type columns. For string columns, a value of 1 indicates character-length semantics and 0 indicates byte-length semantics.

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

The object ID of the table column.

</td>
</tr>
<tr>
<td valign="top">

max\_identity

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

The largest value of the column, if it’s an AUTOINCREMENT, IDENTITY, or GLOBAL AUTOINCREMENT column.

</td>
</tr>
<tr>
<td valign="top">

column\_name

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

The name of the column.

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

The default value for the column. This value, if specified, is only used when an INSERT statement doesn’t specify a value for the column.

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

The data type, if the column is defined using a user-defined data type.

</td>
</tr>
<tr>
<td valign="top">

column\_type

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

The type of column \(C=computed column, and R=other columns\).

</td>
</tr>
<tr>
<td valign="top">

compressed

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

Whether this column is stored in a compressed format.

</td>
</tr>
<tr>
<td valign="top">

collect\_stats

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

Whether the system automatically collects and updates statistics on this column.

</td>
</tr>
<tr>
<td valign="top">

inline\_max

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

The maximum number of bytes of a BLOB to store in a row. A NULL value indicates that either the default value has been applied, or that the column isn’t a character or binary type. A non-NULL inline\_max value corresponds to the INLINE value specified for the column using the CREATE TABLE or ALTER TABLE statement.

</td>
</tr>
<tr>
<td valign="top">

inline\_long

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

The number of duplicate bytes of a BLOB to store in a row if the BLOB size exceeds the inline\_max value. A NULL value indicates that either the default value has been applied, or that the column isn’t a character or binary type. A non-NULL inline\_long value corresponds to the PREFIX value specified for the column using the CREATE TABLE or ALTER TABLE statement.

</td>
</tr>
<tr>
<td valign="top">

lob\_index

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

Whether to build indexes on BLOB values in the column that exceed an internal threshold size \(approximately eight database pages\). A NULL value indicates either that the default is applied, or that the column isn’t BLOB type. A value of 1 indicates that indexes will be built. A value of 0 indicates that no indexes will be built. A non-NULL lob\_index value corresponds to whether INDEX or NO INDEX was specified for the column using the CREATE TABLE or ALTER TABLE statement.

</td>
</tr>
<tr>
<td valign="top">

base\_type\_str

</td>
<td valign="top">

VARCHAR\(32,767\)

</td>
<td valign="top">

The annotated type string representing the physical type of the column.

</td>
</tr>
<tr>
<td valign="top">

nonmaterialized\_value

</td>
<td valign="top">

LONG BINARY

</td>
<td valign="top">

Internal use only.

</td>
</tr>
<tr>
<td valign="top">

start\_schema

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The first version of the table schema in which this column exists.

</td>
</tr>
</table>

**Related Information**  


[SYSTABCOL System View for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/b48617e016a04f69953a0bdf8c812ab7.html "The SYS.SYSTABCOL system view contains one row for each column of each table and view in the database.") :arrow_upper_right:

