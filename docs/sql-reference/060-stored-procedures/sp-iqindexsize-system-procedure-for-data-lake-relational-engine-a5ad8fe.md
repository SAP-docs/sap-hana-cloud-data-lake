<!-- loioa5ad8fe784f21015bda0e710013b6646 -->

# sp\_iqindexsize System Procedure for Data Lake Relational Engine

Gives the size of the specified index.



<a name="loioa5ad8fe784f21015bda0e710013b6646__section_p4t_vqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqindexsize ( '[ <owner>.<table_name>.]<index_name> ' )
```



<a name="loioa5ad8fe784f21015bda0e710013b6646__sp_iqindexsize_parm1"/>

## Parameters


<dl>
<dt><b>

*<owner\>*

</b></dt>
<dd>

The owner of the table.



</dd><dt><b>

*<table\_name\>*

</b></dt>
<dd>

The name of the table.



</dd><dt><b>

*<index\_name\>*

</b></dt>
<dd>

The name of the index.



</dd>
</dl>



<a name="loioa5ad8fe784f21015bda0e710013b6646__sp_iqindexsize_returns1"/>

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

`Username`

</td>
<td valign="top">

Index owner.

</td>
</tr>
<tr>
<td valign="top">

`Indexname`

</td>
<td valign="top">

Index for which results are returned, including the table name.

</td>
</tr>
<tr>
<td valign="top">

`Type`

</td>
<td valign="top">

Index type.

</td>
</tr>
<tr>
<td valign="top">

`Info`

</td>
<td valign="top">

Component of the data lake Relational Engine index for which the KBytes, Pages, and Compressed Pages are being reported. The components vary by index type. For example, the default \(FP\) index includes BARRAY \(barray\) and Bitmap \(bm\) components.

</td>
</tr>
<tr>
<td valign="top">

`KBytes`

</td>
<td valign="top">

An approximation of the physical table size, in kilobytes. Data lake Relational Engine uses a 512KB page size and the size in KB reported by sp\_iqtablesize is based on a heuristic for the average page size in the cloud dbspace.

</td>
</tr>
<tr>
<td valign="top">

`Pages`

</td>
<td valign="top">

Number of data lake Relational Engine pages needed to hold the object in memory.

</td>
</tr>
<tr>
<td valign="top">

`Compressed Pages`

</td>
<td valign="top">

Number of data lake Relational Engine pages when the object is compressed \(on disk\).

</td>
</tr>
</table>



<a name="loioa5ad8fe784f21015bda0e710013b6646__sp_iqindexsize_remarks1"/>

## Remarks

Returns the total size of the index in bytes and kilobytes, and an Info column that describes the component of the data lake Relational Engine index for which the KBytes, Pages, and Compressed Pages are reported. The components described vary by index type. For example, the default \(FP\) index includes BARRAY \(barray\) and Bitmap \(bm\) components.

Also returns the number of pages required to hold the object in memory and the number of data lake Relational Engine pages when the index is compressed \(on disk\).

You must specify the *<index\_name\>* parameter with this procedure. To restrict results to this index name in a single table, include *<owner.table.\>* when specifying the index.



<a name="loioa5ad8fe784f21015bda0e710013b6646__sp_iqindexsize_priv1"/>

## Privileges



### 

Requires EXECUTE object-level privilege on this procedure along with one of the following:

-   You won the object referenced by the index.
-   ALTER ANY INDEX system privilege



<a name="loioa5ad8fe784f21015bda0e710013b6646__sp_iqindexsize_sideeffects1"/>

## Side Effects

None.



<a name="loioa5ad8fe784f21015bda0e710013b6646__sp_iqindexsize_examples1"/>

## Examples

```
--- Setup for the following examples ---
CREATE TEXT INDEX IDX_EMPLOYEES ON EMPLOYEES( CITY ) IMMEDIATE REFRESH;
```

This example returns information on the index IDX\_H2.

```
CALL sp_iqindexsize ('IDX_EMPLOYEES');
```


<table>
<tr>
<th valign="top">

Username

</th>
<th valign="top">

Indexname

</th>
<th valign="top">

Type

</th>
<th valign="top">

Info

</th>
<th valign="top">

KBytes

</th>
<th valign="top">

Pages

</th>
<th valign="top">

CompressedPages

</th>
</tr>
<tr>
<td valign="top">

USER1

</td>
<td valign="top">

USER1.EMPLOYEES.CITY

</td>
<td valign="top">

TEXT

</td>
<td valign="top">

Total

</td>
<td valign="top">

896

</td>
<td valign="top">

12

</td>
<td valign="top">

6

</td>
</tr>
<tr>
<td valign="top">

USER1

</td>
<td valign="top">

USER1.EMPLOYEES.CITY

</td>
<td valign="top">

TEXT

</td>
<td valign="top">

vdo

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

USER1

</td>
<td valign="top">

USER1.EMPLOYEES.CITY

</td>
<td valign="top">

TEXT

</td>
<td valign="top">

bt

</td>
<td valign="top">

304

</td>
<td valign="top">

4

</td>
<td valign="top">

2

</td>
</tr>
<tr>
<td valign="top">

USER1

</td>
<td valign="top">

USER1.EMPLOYEES.CITY

</td>
<td valign="top">

TEXT

</td>
<td valign="top">

garray

</td>
<td valign="top">

152

</td>
<td valign="top">

2

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

USER1

</td>
<td valign="top">

USER1.EMPLOYEES.CITY

</td>
<td valign="top">

TEXT

</td>
<td valign="top">

bm

</td>
<td valign="top">

136

</td>
<td valign="top">

2

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

USER1

</td>
<td valign="top">

USER1.EMPLOYEES.CITY

</td>
<td valign="top">

TEXT

</td>
<td valign="top">

barray

</td>
<td valign="top">

152

</td>
<td valign="top">

2

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

USER1

</td>
<td valign="top">

USER1.EMPLOYEES.CITY

</td>
<td valign="top">

TEXT

</td>
<td valign="top">

dpstore

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

USER1

</td>
<td valign="top">

USER1.EMPLOYEES.CITY

</td>
<td valign="top">

TEXT

</td>
<td valign="top">

largelob

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

USER1

</td>
<td valign="top">

USER1.EMPLOYEES.CITY

</td>
<td valign="top">

TEXT

</td>
<td valign="top">

txtPst

</td>
<td valign="top">

304

</td>
<td valign="top">

4

</td>
<td valign="top">

2

</td>
</tr>
</table>

**Related Information**  


[sp\_iqindexmetadata System Procedure for Data Lake Relational Engine](sp-iqindexmetadata-system-procedure-for-data-lake-relational-engine-a5ad0e4.md "Displays index metadata for a given index.")

[sp\_iqindexfragmentation System Procedure for Data Lake Relational Engine](sp-iqindexfragmentation-system-procedure-for-data-lake-relational-engine-a5ac10a.md "Reports information about the percentage of page space taken up within the B-trees, garrays, and bitmap structures in data lake Relational Engine indexes.")

[sp\_iqindexinfo System Procedure for Data Lake Relational Engine](sp-iqindexinfo-system-procedure-for-data-lake-relational-engine-a5ac909.md "Displays the number of blocks (objects) used per index per main dbspace for a given object. If the object resides on several dbspaces, sp_iqindexinfo returns the space used in all dbspaces, as shown in the example.")

