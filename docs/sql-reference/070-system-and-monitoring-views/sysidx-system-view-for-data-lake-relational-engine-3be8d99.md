<!-- loio3be8d99a6c5f10149158a1c4b55629f2 -->

# SYSIDX System View for Data Lake Relational Engine

Each row in the SYSIDX system view defines a logical index in the database. The underlying system table for this view is ISYSIDX.



<a name="loio3be8d99a6c5f10149158a1c4b55629f2__section_z1x_wv3_g4b"/>

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

Uniquely identifies the table to which this index applies.

</td>
</tr>
<tr>
<td valign="top">

index\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

A unique number identifying the index within its table.

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

The internal ID for the index, uniquely identifying it in the database.

</td>
</tr>
<tr>
<td valign="top">

phys\_index\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

Identifies the underlying physical index used to implement the logical index. This value is NULL for indexes on temporary tables or remote tables. Otherwise, the value corresponds to the object\_id of a physical index in the SYSPHYSIDX system view.

</td>
</tr>
<tr>
<td valign="top">

dbspace\_id

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

The ID of the file in which the index is contained. This value corresponds to an entry in the SYSDBSPACE system view.

</td>
</tr>
<tr>
<td valign="top">

index\_category

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

The type of index. Values include:


<dl>
<dt><b>

1

</b></dt>
<dd>

Primary key



</dd><dt><b>

2

</b></dt>
<dd>

Foreign key



</dd><dt><b>

3

</b></dt>
<dd>

Secondary index \(includes unique constraints\)



</dd><dt><b>

4

</b></dt>
<dd>

Text indexes



</dd>
</dl>



</td>
</tr>
<tr>
<td valign="top">

"unique"

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

Indicates whether the index is a unique index \(1\), a unique constraint \(2\), reserved \(3\), a non-unique index \(4\), or a unique index WITH NULLS NOT DISTINCT \(5\).

</td>
</tr>
<tr>
<td valign="top">

index\_name

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

The name of the index.

</td>
</tr>
<tr>
<td valign="top">

not\_enforced

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

For internal use only.

</td>
</tr>
<tr>
<td valign="top">

file\_id

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

DEPRECATED. This column is present in SYSVIEW, but not in the underlying system table ISYSIDX. The contents of this column are the same as dbspace\_id, and it is provided for compatibility. Use dbspace\_id instead.

</td>
</tr>
</table>

**Related Information**  


[SYSIDX System View for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/d4837fc57359426082842b1ba1a855f2.html "Each row in the SYSIDX system view defines a logical index in the database. The underlying system table for this view is ISYSIDX.") :arrow_upper_right:

