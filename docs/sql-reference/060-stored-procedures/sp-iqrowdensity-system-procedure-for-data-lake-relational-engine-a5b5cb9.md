<!-- loioa5b5cb9b84f2101585b8e3b5e25893af -->

# sp\_iqrowdensity System Procedure for Data Lake Relational Engine

Reports information about the internal row fragmentation for a table at the FP index level.



<a name="loioa5b5cb9b84f2101585b8e3b5e25893af__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqrowdensity ( '
   { TABLE [ { <owner> | <schema-name> }.]<table-name> 
   | ( COLUMN <column-name>[ COLUMN <column-name>[ ...] ] }
   ' )
```



<a name="loioa5b5cb9b84f2101585b8e3b5e25893af__iq_refbb_1747"/>

## Parameters


<dl>
<dt><b>

*<table-name\>*

</b></dt>
<dd>

Reports on all columns in the named table. You can't specify multiple tables.



</dd><dt><b>

*<column-name\>*

</b></dt>
<dd>

Reports on the named column in the target table. You may specify multiple target columns, but must repeat the COLUMN keyword each time.



</dd>
</dl>



<a name="loioa5b5cb9b84f2101585b8e3b5e25893af__section_hq1_lrz_kbc"/>

## Result Set


<table>
<tr>
<th valign="top">

Column Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Tablename

</td>
<td valign="top">

Displays the table name.

</td>
</tr>
<tr>
<td valign="top">

Column Name

</td>
<td valign="top">

Displays the column name.

</td>
</tr>
<tr>
<td valign="top">

IndexType

</td>
<td valign="top">

Displays the type of index on the column.

</td>
</tr>
<tr>
<td valign="top">

Density

</td>
<td valign="top">

Displays the density of the row.

</td>
</tr>
</table>



<a name="loioa5b5cb9b84f2101585b8e3b5e25893af__iq_refbb_1749"/>

## Remarks

The keywords TABLE and COLUMN are not case-sensitive.

sp\_iqrowdensity measures row fragmentation at the default index level. Density is the ratio of the minimum number of pages required by an index for existing table rows to the number of pages actually used by the index. This procedure returns density as a number such that 0 < density < 1. For example, if an index that requires 8 pages minimum storage occupies 10 pages, its density is .8.

The density reported does not indicate the number of disk pages that may be reclaimed by re-creating or reorganizing the default index.

This procedure displays information about the row density of a column, but does not recommend further action. You must determine whether or not to re-create, reorganize, or rebuild an index.

The IndexType column in the results set always returns the maximum number of bits required to encode the column.

Unlike the FP\(1\), FP\(2\), FP\(3\) dictionary compression in previous releases, which uses the same number of bits for each page, NBit encodes each page dynamically. sp\_iqrowdensity always returns the largest number of bits used among all of the pages



<a name="loioa5b5cb9b84f2101585b8e3b5e25893af__iq_refbb_1746"/>

## Privileges

Requires EXECUTE object-level privilege on this procedure, along with one of the following:

-   You own the object.
-   ALTER ANY INDEX system privilege
-   ALTER ANY OBJECT system privilege
-   CREATE ANY INDEX system privilege
-   CREATE ANY OBJECT system privilege
-   MANAGE ANY DBSPACE system privilege
-   MONITOR system privilege



## Side Effects

None.



<a name="loioa5b5cb9b84f2101585b8e3b5e25893af__iq_refbb_1750"/>

## Examples

This example returns the row density on table SALESORDERS:

```
CALL sp_iqrowdensity(TABLE SALESORDERS');
```


<table>
<tr>
<th valign="top" rowspan="1">

Tablename

</th>
<th valign="top" rowspan="1">

Column Name

</th>
<th valign="top" rowspan="1">

IndexType

</th>
<th valign="top" rowspan="1">

Density

</th>
</tr>
<tr>
<td valign="top" rowspan="1">

USER1.SALESORDERS

</td>
<td valign="top" rowspan="1">

ORDER\_ID

</td>
<td valign="top" rowspan="1">

NBit FP

</td>
<td valign="top" rowspan="1">

1.0

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

USER1.SALESORDERS

</td>
<td valign="top" rowspan="1">

ORDER\_DESC

</td>
<td valign="top" rowspan="1">

NBit FP

</td>
<td valign="top" rowspan="1">

1.0

</td>
</tr>
</table>

This example returns the row density on columns DEPARTMENT\_ID and DEPARTMENT\_NAME in table DEPARTMENTS:

```
CALL sp_iqrowdensity('COLUMN DEPARTMENTS.DEPARTMENTID COLUMN DEPARTMENT.DEPARTMENTNAME ');
```


<table>
<tr>
<th valign="top" rowspan="1">

Tablename

</th>
<th valign="top" rowspan="1">

Column Name

</th>
<th valign="top" rowspan="1">

IndexType

</th>
<th valign="top" rowspan="1">

Density

</th>
</tr>
<tr>
<td valign="top" rowspan="1">

USER1.DEPARTMENT

</td>
<td valign="top" rowspan="1">

DEPARTMENT\_ID

</td>
<td valign="top" rowspan="1">

NBit FP

</td>
<td valign="top" rowspan="1">

1.0

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

USER1.DEPARTMENT

</td>
<td valign="top" rowspan="1">

DEPARTMENT\_NAME

</td>
<td valign="top" rowspan="1">

NBit FP

</td>
<td valign="top" rowspan="1">

1.0

</td>
</tr>
</table>

**Related Information**  


[sp\_iqindexfragmentation System Procedure for Data Lake Relational Engine](sp-iqindexfragmentation-system-procedure-for-data-lake-relational-engine-a5ac10a.md "Reports information about the percentage of page space taken up within the B-trees, garrays, and bitmap structures in data lake Relational Engine indexes.")

[sp\_iqrebuildindex System Procedure for Data Lake Relational Engine](sp-iqrebuildindex-system-procedure-for-data-lake-relational-engine-a5b342e.md "Rebuilds column indexes.")

