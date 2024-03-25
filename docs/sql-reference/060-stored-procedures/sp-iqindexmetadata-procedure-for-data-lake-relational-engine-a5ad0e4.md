<!-- loioa5ad0e4b84f21015866c8fef1c8fee50 -->

# sp\_iqindexmetadata Procedure for Data Lake Relational Engine

Displays index metadata for a given index.



<a name="loioa5ad0e4b84f21015866c8fef1c8fee50__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
hdladmin.sp_iqindexmetadata ( '<index-name>'
   [, '<table-name>' [, '<owner-name>' ] ] )
```



<a name="loioa5ad0e4b84f21015866c8fef1c8fee50__section_bps_vg1_lcb"/>

## Parameter


<dl>
<dt><b>

*<index-name\>*

</b></dt>
<dd>

For all indexes except FP, use the text name defined for the index. For FP indexes, use the name of the index as defined in the iname column of the sysindex table. Run <code>SELECT * FROM SYS.SYSINDEXES WHERE TNAME=<i class="varname">&lt;table_name&gt;</i></code> to display the value.



</dd>
</dl>



<a name="loioa5ad0e4b84f21015866c8fef1c8fee50__section_ecl_j35_xyb"/>

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

Value1

</td>
<td valign="top">

The table owner.

</td>
</tr>
<tr>
<td valign="top">

Value2

</td>
<td valign="top">

The table name.

</td>
</tr>
<tr>
<td valign="top">

Value3

</td>
<td valign="top">

The index name.

</td>
</tr>
</table>

Additional output is index type specific.


<table>
<tr>
<th valign="top">

Index Type

</th>
<th valign="top">

Metadata Returned

</th>
</tr>
<tr>
<td valign="top">

CMP, DATE, DTTM, TIME

</td>
<td valign="top">

Type, Version

</td>
</tr>
<tr>
<td valign="top">

FP

</td>
<td valign="top">

Type, Style, Version, DBType, Maximum Width, EstUnique, TokenCount, NBit, CountSize, DictSize, CountLen, MaxKeyToken, MinKey Token, MinCount, MaxCount, DistinctKey, BArray Version, RidMap Version, IQ Unique

</td>
</tr>
<tr>
<td valign="top">

HG

</td>
<td valign="top">

Type, Version, Maintains Exact Distinct, Level 0 Threshold, Force Physical Delete, Maximum Level Count, Tier ratio, Auto sizing, Average Load Size \(records\), Active Subindex count, Cardinality Range Min - Max, Estimated Cardinality, Accuracy of Cardinality

</td>
</tr>
<tr>
<td valign="top">

LF

</td>
<td valign="top">

Type, Version, IndexStatus, NumberOfBlockmaps, BitsPerBlockmap, Distinct Keys

</td>
</tr>
<tr>
<td valign="top">

WD

</td>
<td valign="top">

Type, Version, KeySize, Delimiters, DelimiterCount, MaxKeyWordLength, PermitEmptyWord

</td>
</tr>
</table>



<a name="loioa5ad0e4b84f21015866c8fef1c8fee50__iq_refbb_1614"/>

## Remarks

You can optionally restrict the output to only those indexes on a specified table, and to only those indexes belonging to a specified owner.

Specifying a table name limits output to those indexes belonging to that table. Specifying an owner name limits output to indexes owned by that owner. Omitted parameters default to NULL. You can specify only one index per procedure.

User supplier IQ UNIQUE value for the column is available through sp\_iqindexmetadata. It reports exact cardinality if Unique HG are present. It reports 0 as cardinality if \(only\) non-unique HG is present.



<a name="loioa5ad0e4b84f21015866c8fef1c8fee50__iq_refbb_1613"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure, along with one of the following:

-   You own the object.
-   ALTER ANY INDEX system privilege
-   ALTER ANY OBJECT system privilege
-   REFERENCES object-level privilege on the table



<a name="loioa5ad0e4b84f21015866c8fef1c8fee50__section_lgv_1c1_nbb"/>

## Side Effects

None



<a name="loioa5ad0e4b84f21015866c8fef1c8fee50__iq_refbb_1617"/>

## Examples

This example determines the name of the FP index for column C1 on table table1 and then displays the metadata of the index. First, determine the iname value for the FP index.

```
SELECT * FROM SYS.SYSINDEXES WHERE tname='table1';
```


<table>
<tr>
<th valign="top">

icreator

</th>
<th valign="top">

iname

</th>
<th valign="top">

fname

</th>
<th valign="top">

creator

</th>
<th valign="top">

tname

</th>
</tr>
<tr>
<td valign="top">

USER1

</td>
<td valign="top">

ASIQ\_ID\_T1759\_C1\_FP

</td>
<td valign="top">

user\_object\_store

</td>
<td valign="top">

USER1

</td>
<td valign="top">

table1

</td>
</tr>
<tr>
<td valign="top">

USER1

</td>
<td valign="top">

ASIQ\_ID\_T1759\_C2\_FP

</td>
<td valign="top">

user\_object\_store

</td>
<td valign="top">

USER1

</td>
<td valign="top">

table1

</td>
</tr>
<tr>
<td valign="top">

USER1

</td>
<td valign="top">

HG1

</td>
<td valign="top">

user\_object\_store

</td>
<td valign="top">

USER1

</td>
<td valign="top">

table1

</td>
</tr>
</table>

Then, display the metadata for the FP index on the table.

```
CALL sp_iqindexmetadata ('ASIQ_IDX_T1759_C1_FP','table1',USER1);
```


<table>
<tr>
<th valign="top">

Value1

</th>
<th valign="top">

Value2

</th>
<th valign="top">

Value3

</th>
</tr>
<tr>
<th valign="top">

USER1

</th>
<th valign="top">

table1

</th>
<th valign="top">

ASIQ\_IDX\_T1759\_C1\_FP

</th>
</tr>
<tr>
<td valign="top">

\-------------------------------

</td>
<td valign="top">

\-------------------------------

</td>
<td valign="top">

\-------------------------------

</td>
</tr>
<tr>
<td valign="top">

Type

</td>
<td valign="top">

FP

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Style

</td>
<td valign="top">

NBit FP

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Version

</td>
<td valign="top">

4

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

DBType

</td>
<td valign="top">

11

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Maximum Width

</td>
<td valign="top">

0

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

EstUnique

</td>
<td valign="top">

0

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

TokenCount

</td>
<td valign="top">

0

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

NBit

</td>
<td valign="top">

1

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

CountSize

</td>
<td valign="top">

0

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

DictSize

</td>
<td valign="top">

0

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

CountLen

</td>
<td valign="top">

4

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

MaxKeyToken

</td>
<td valign="top">

0

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

MinKeyToken

</td>
<td valign="top">

0

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

MinCount

</td>
<td valign="top">

0

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

MaxCount

</td>
<td valign="top">

0

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

DistinctKey

</td>
<td valign="top">

0

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

BArray Version

</td>
<td valign="top">

2

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

RidMap Version

</td>
<td valign="top">

1

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

IQ Unique

</td>
<td valign="top">

0

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

\-------------------------------

</td>
<td valign="top">

\-------------------------------

</td>
<td valign="top">

\-------------------------------

</td>
</tr>
<tr>
<td valign="top">

===================

</td>
<td valign="top">

===================

</td>
<td valign="top">

===================

</td>
</tr>
</table>

This example displays the metadata for the high group index HG1 on table table1.

```
CALL sp_iqindexmetadata ('HG1','table1',USER1);
```


<table>
<tr>
<th valign="top">

Value1

</th>
<th valign="top">

Value2

</th>
<th valign="top">

Value3

</th>
</tr>
<tr>
<td valign="top">

USER1

</td>
<td valign="top">

table1

</td>
<td valign="top">

HG1

</td>
</tr>
<tr>
<td valign="top">

\-------------------------------

</td>
<td valign="top">

\-------------------------------

</td>
<td valign="top">

\-------------------------------

</td>
</tr>
<tr>
<td valign="top">

Type

</td>
<td valign="top">

HG

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Version

</td>
<td valign="top">

3

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Maintains Exact Distinct

</td>
<td valign="top">

Yes

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Level 0 Threshold

</td>
<td valign="top">

No threshold

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Force Physical Delete

</td>
<td valign="top">

Yes

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Maximum Level Count

</td>
<td valign="top">

1

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Tier ratio

</td>
<td valign="top">

1

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Auto sizing

</td>
<td valign="top">

Off

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Average Load Size \(records\)

</td>
<td valign="top">

Not determined yet

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Active Subindex count

</td>
<td valign="top">

0

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Cardinality Range Min - Max

</td>
<td valign="top">

0-0

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Estimated Cardinality

</td>
<td valign="top">

0

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Accuracy of Cardinality \(%\)

</td>
<td valign="top">

100

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

\-------------------------------

</td>
<td valign="top">

\-------------------------------

</td>
<td valign="top">

\-------------------------------

</td>
</tr>
<tr>
<td valign="top">

===================

</td>
<td valign="top">

===================

</td>
<td valign="top">

===================

</td>
</tr>
</table>

**Related Information**  


[sp\_iqindexfragmentation Procedure for Data Lake Relational Engine](sp-iqindexfragmentation-procedure-for-data-lake-relational-engine-a5ac10a.md "Reports information about the percentage of page space taken up within the B-trees, garrays, and bitmap structures in data lake Relational Engine indexes.")

[sp\_iqindexinfo Procedure for Data Lake Relational Engine](sp-iqindexinfo-procedure-for-data-lake-relational-engine-a5ac909.md "Displays the number of blocks (objects) used per index per main dbspace for a given object. If the object resides on several dbspaces, sp_iqindexinfo returns the space used in all dbspaces, as shown in the example.")

[sp\_iqindexsize Procedure for Data Lake Relational Engine](sp-iqindexsize-procedure-for-data-lake-relational-engine-a5ad8fe.md "Gives the size of the specified index.")

[sp\_iqcolumnmetadata Procedure for Data Lake Relational Engine](sp-iqcolumnmetadata-procedure-for-data-lake-relational-engine-a87e284.md "Returns details about column indexes in one or more tables.")

