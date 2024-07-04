<!-- loioa5d1bd5684f2101581e2c9c8b4c4669b -->

# SYSIQTABCOL System View for Data Lake Relational Engine

Presents group information from `ISYSIQTABCOL` in a readable format. Each row in the SYSIQTABCOL view describes a column in an IQ table.



<a name="loioa5d1bd5684f2101581e2c9c8b4c4669b__section_g1z_xv3_g4b"/>

## Usage

This data lake Relational Engine system view can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



> ### Note:  
> This view replaces the deprecated system view SYSIQCOLUMN.


<table>
<tr>
<th valign="top">

Column Name

</th>
<th valign="top">

Column Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

link\_table\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

For internal use.

</td>
</tr>
<tr>
<td valign="top">

link\_column\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

For internal use.

</td>
</tr>
<tr>
<td valign="top">

max\_length

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

Indicates the maximum length allowed by the column.

</td>
</tr>
<tr>
<td valign="top">

approx\_unique\_count

</td>
<td valign="top">

ROWID

</td>
<td valign="top">

Approximate number of unique values \(cardinality\) of this column.

</td>
</tr>
<tr>
<td valign="top">

cardinality

</td>
<td valign="top">

ROWID

</td>
<td valign="top">

The actual number of unique values \(cardinality\) of this column.

</td>
</tr>
<tr>
<td valign="top">

has\_data

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

Indicates that the column contains data \(T/F\).

</td>
</tr>
<tr>
<td valign="top">

is\_nbit

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

Indicates whether the column is NBit \(T\) or Flat FP \(F\).

</td>
</tr>
</table>



<a name="loioa5d1bd5684f2101581e2c9c8b4c4669b__SYSIQTABCOL_remarks1"/>

## Remarks

```
ALTER VIEW "SYS"."SYSIQTABCOL"
                    as select * from SYS.ISYSIQTABCOL;
```



<a name="loioa5d1bd5684f2101581e2c9c8b4c4669b__SYSIQTABCOL_constraints1"/>

## Constraints on Underlying System Table

```
Primary key (table_id);
```

**Related Information**  


[SYSIQTABCOL System View for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/8387df93bb6c4a87acd9138dbaa18ba9.html "Presents group information from ISYSIQTABCOL in a readable format. Each row in the SYSIQTABCOL view describes a column in an IQ table.") :arrow_upper_right:

