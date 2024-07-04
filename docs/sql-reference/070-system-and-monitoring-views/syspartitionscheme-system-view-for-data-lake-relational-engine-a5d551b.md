<!-- loioa5d551b784f21015b3eabb10e5074fd2 -->

# SYSPARTITIONSCHEME System View for Data Lake Relational Engine

Presents group information from `ISYSPARTITIONSCHEME` in a readable format.



<a name="loioa5d551b784f21015b3eabb10e5074fd2__section_vwg_vhq_b4b"/>

## Usage

This data lake Relational Engine system view can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




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

partitioned\_object\_id

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

Each partitioned object \(table\) is assigned a unique number.

</td>
</tr>
<tr>
<td valign="top">

partition\_method

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

Partitioning method for this table. Valid values:

-   1 – for range
-   3 – for hash \(2 is unused\)



</td>
</tr>
<tr>
<td valign="top">

subpartition\_method

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

Subpartitioning method for this table. Valid values:

-   NULL - no subpartitioning
-   1 – for range partitioning
-   3 – for hash partitioning \(2 is unused\)



</td>
</tr>
</table>



<a name="loioa5d551b784f21015b3eabb10e5074fd2__SYSPARTITIONSCHEME_remarks1"/>

## Remarks

Each row in the `SYSPARTITIONSCHEME` view describes a partitioned object \(table or index\) in the database.

```
ALTER VIEW "SYS"."SYSPARTITIONSCHEME"
as select * from SYS.ISYSPARTITIONSCHEME;
```



<a name="loioa5d551b784f21015b3eabb10e5074fd2__SYSPARTITIONSCHEME_contstraints"/>

## Constraints on Underlying System Table

```
Primary key (partitioned_object_id);
```

```
Foreign key (partitioned_object_id) references SYS.ISYSOBJECT;
```

**Related Information**  


[SYSPARTITIONSCHEME System View for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/4f05e41823a145a4812e4bb783bdc650.html "Presents group information from ISYSPARTITIONSCHEME in a readable format.") :arrow_upper_right:

