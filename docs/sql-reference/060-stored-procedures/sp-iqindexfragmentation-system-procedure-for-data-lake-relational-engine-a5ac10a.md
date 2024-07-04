<!-- loioa5ac10a084f210158b30b3fa5c350b40 -->

# sp\_iqindexfragmentation System Procedure for Data Lake Relational Engine

Reports information about the percentage of page space taken up within the B-trees, garrays, and bitmap structures in data lake Relational Engine indexes.



<a name="loioa5ac10a084f210158b30b3fa5c350b40__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqindexfragmentation ( '<target>' )
```



<a name="loioa5ac10a084f210158b30b3fa5c350b40__iq_refbb_1603"/>

## Parameters


<dl>
<dt><b>

*<target\>*

</b></dt>
<dd>

```
'<target> ::=
   { TABLE [ { <owner-name> | <schema-name> }.]<table-name>
   | INDEX <index-name> [ INDEX <index-name> ] [...] }
```



</dd><dt><b>

*<table-name\>*

</b></dt>
<dd>

<code>TABLE <i class="varname">&lt;table-name&gt;</i></code> reports on all nondefault indexes in the named table.



</dd><dt><b>

*<index-name\>*

</b></dt>
<dd>

<code>INDEX <i class="varname">&lt;index-name&gt;</i></code> reports on the named index. Each *<index-name\>* is a qualified index name. You can specify multiple indexes within the table, but you must repeat the `INDEX` keyword with each index specified.



</dd>
</dl>



<a name="loioa5ac10a084f210158b30b3fa5c350b40__section_bt5_jg3_vzb"/>

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

Index

</td>
<td valign="top">

Name of the index.

</td>
</tr>
<tr>
<td valign="top">

IndexType

</td>
<td valign="top">

Type of index.

</td>
</tr>
<tr>
<td valign="top">

Btree\_Node\_pages

</td>
<td valign="top">

Number of pages.

</td>
</tr>
<tr>
<td valign="top">

GARRAY\_FILL\_FACTOR\_PERCENT

</td>
<td valign="top">

Value of the GARRAY\_FILL\_FACTOR\_PERCENT option.

</td>
</tr>
</table>



<a name="loioa5ac10a084f210158b30b3fa5c350b40__section_evb_vcz_mbb"/>

## Remarks

For garrays, the fill percentage calculation does not take into account the reserved space within the garray groups, which is controlled by the GARRAY\_FILL\_FACTOR\_PERCENT option.

> ### Note:  
> All percentages are truncated to the nearest percentage point. HG indexes also display the value of option GARRAY\_FILL\_FACTOR\_PERCENT. Index types that use a B-tree also display the number of node \(nonleaf\) pages. These are HG, WD, DATE, and DTTM.
> 
> If an error occurs during execution of this stored procedure, the SQLCODE would be nonzero.



<a name="loioa5ac10a084f210158b30b3fa5c350b40__iq_refbb_1602"/>

## Privileges

Requires all of the following:

-   EXECUTE object-level privilege on this procedure
-   MANAGE ANY DBSPACE system privilege



<a name="loioa5ac10a084f210158b30b3fa5c350b40__section_cs5_fc1_nbb"/>

## Side Effects

None.



<a name="loioa5ac10a084f210158b30b3fa5c350b40__iq_refbb_1605"/>

## Examples

This example returns the internal index fragmentation for the HG index IDX\_HG\_C1.

```
CALL sp_iqindexfragmentation ( INDEX IDX_HG_C1' );
```


<table>
<tr>
<th valign="top">

Index

</th>
<th valign="top">

IndexType

</th>
<th valign="top">

Btree\_Node\_pages

</th>
<th valign="top">

GARRAY\_FILL\_FACTOR\_PERCENT

</th>
</tr>
<tr>
<td valign="top">

USER1.C1.IDX\_HG\_C1

</td>
<td valign="top">

HG

</td>
<td valign="top">

8

</td>
<td valign="top">

25

</td>
</tr>
<tr>
<td valign="top">

SQLCODE:

</td>
<td valign="top">

0

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Fill Percent

</td>
<td valign="top">

btree pages

</td>
<td valign="top">

garray pages

</td>
<td valign="top">

bitmap pages

</td>
</tr>
<tr>
<td valign="top">

0-10%

</td>
<td valign="top">

13

</td>
<td valign="top">

2

</td>
<td valign="top">

8

</td>
</tr>
<tr>
<td valign="top">

11-20%

</td>
<td valign="top">

1

</td>
<td valign="top">

8

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

21-30%

</td>
<td valign="top">

0

</td>
<td valign="top">

4

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

31-40%

</td>
<td valign="top">

3

</td>
<td valign="top">

20

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

41-50%

</td>
<td valign="top">

4

</td>
<td valign="top">

116

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

51-60%

</td>
<td valign="top">

6

</td>
<td valign="top">

4

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

61-70%

</td>
<td valign="top">

3

</td>
<td valign="top">

3

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

71-80%

</td>
<td valign="top">

4

</td>
<td valign="top">

1

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

81-90%

</td>
<td valign="top">

1

</td>
<td valign="top">

1

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

91-100%

</td>
<td valign="top">

192

</td>
<td valign="top">

276

</td>
<td valign="top">

0

</td>
</tr>
</table>

This example returns the internal index fragmentation for all indexes on table C1. There are two indexes on the table, IDX\_HG\_C1 and IDX\_DATE\_C1.

```
CALL sp_iqindexfragmentation ( 'TABLE C1' );
```


<table>
<tr>
<th valign="top">

Index

</th>
<th valign="top">

IndexType

</th>
<th valign="top">

Btree\_Node\_pages

</th>
<th valign="top">

GARRAY\_FILL\_FACTOR\_PERCENT

</th>
</tr>
<tr>
<td valign="top">

USER1.C1.IDX\_HG\_C1

</td>
<td valign="top">

Unique HG

</td>
<td valign="top">

0

</td>
<td valign="top">

25

</td>
</tr>
<tr>
<td valign="top">

SQLCODE:

</td>
<td valign="top">

0

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Fill Percent

</td>
<td valign="top">

btree pages

</td>
<td valign="top">

garray pages

</td>
<td valign="top">

bitmap pages

</td>
</tr>
<tr>
<td valign="top">

0-10%

</td>
<td valign="top">

13

</td>
<td valign="top">

2

</td>
<td valign="top">

8

</td>
</tr>
<tr>
<td valign="top">

11-20%

</td>
<td valign="top">

1

</td>
<td valign="top">

8

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

21-30%

</td>
<td valign="top">

0

</td>
<td valign="top">

4

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

31-40%

</td>
<td valign="top">

3

</td>
<td valign="top">

20

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

41-50%

</td>
<td valign="top">

4

</td>
<td valign="top">

116

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

51-60%

</td>
<td valign="top">

6

</td>
<td valign="top">

4

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

61-70%

</td>
<td valign="top">

3

</td>
<td valign="top">

3

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

71-80%

</td>
<td valign="top">

4

</td>
<td valign="top">

1

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

81-90%

</td>
<td valign="top">

1

</td>
<td valign="top">

1

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

91-100%

</td>
<td valign="top">

192

</td>
<td valign="top">

276

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

========

</td>
<td valign="top">

========

</td>
<td valign="top">

========

</td>
<td valign="top">

========

</td>
</tr>
<tr>
<td valign="top">

USER1.C1.IDX\_DATE\_C1

</td>
<td valign="top">

DATE

</td>
<td valign="top">

0

</td>
<td valign="top">

25

</td>
</tr>
<tr>
<td valign="top">

SQLCODE:

</td>
<td valign="top">

0

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Fill Percent

</td>
<td valign="top">

btree pages

</td>
<td valign="top">

garray pages

</td>
<td valign="top">

bitmap pages

</td>
</tr>
<tr>
<td valign="top">

0-10%

</td>
<td valign="top">

26

</td>
<td valign="top">

4

</td>
<td valign="top">

9

</td>
</tr>
<tr>
<td valign="top">

11-20%

</td>
<td valign="top">

2

</td>
<td valign="top">

8

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

21-30%

</td>
<td valign="top">

0

</td>
<td valign="top">

8

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

31-40%

</td>
<td valign="top">

6

</td>
<td valign="top">

40

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

41-50%

</td>
<td valign="top">

8

</td>
<td valign="top">

150

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

51-60%

</td>
<td valign="top">

12

</td>
<td valign="top">

8

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

61-70%

</td>
<td valign="top">

6

</td>
<td valign="top">

6

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

71-80%

</td>
<td valign="top">

8

</td>
<td valign="top">

3

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

81-90%

</td>
<td valign="top">

2

</td>
<td valign="top">

2

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

91-100%

</td>
<td valign="top">

70

</td>
<td valign="top">

276

</td>
<td valign="top">

0

</td>
</tr>
</table>

This example returns the internal index fragmentation for two specific indexes, IDX\_HG\_C1 and IDX\_HG\_C2. The indexes refer to different tables, C1 and C2.

```
sp_iqindexfragmentation ( 'INDEX IDX_HG_C1 INDEX IDX_HG_C1' );
```


<table>
<tr>
<th valign="top">

Index

</th>
<th valign="top">

IndexType

</th>
<th valign="top">

Btree\_Node\_pages

</th>
<th valign="top">

GARRAY\_FILL\_FACTOR\_PERCENT

</th>
</tr>
<tr>
<td valign="top">

HDLADMIN.C1.idx\_hg\_c1

</td>
<td valign="top">

Unique HG

</td>
<td valign="top">

0

</td>
<td valign="top">

25

</td>
</tr>
<tr>
<td valign="top">

SQLCODE:

</td>
<td valign="top">

0

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Fill Percent

</td>
<td valign="top">

btree pages

</td>
<td valign="top">

garray pages

</td>
<td valign="top">

bitmap pages

</td>
</tr>
<tr>
<td valign="top">

0-10%

</td>
<td valign="top">

13

</td>
<td valign="top">

2

</td>
<td valign="top">

8

</td>
</tr>
<tr>
<td valign="top">

11-20%

</td>
<td valign="top">

1

</td>
<td valign="top">

8

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

21-30%

</td>
<td valign="top">

0

</td>
<td valign="top">

4

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

31-40%

</td>
<td valign="top">

3

</td>
<td valign="top">

20

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

41-50%

</td>
<td valign="top">

4

</td>
<td valign="top">

116

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

51-60%

</td>
<td valign="top">

6

</td>
<td valign="top">

4

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

61-70%

</td>
<td valign="top">

3

</td>
<td valign="top">

3

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

71-80%

</td>
<td valign="top">

4

</td>
<td valign="top">

1

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

81-90%

</td>
<td valign="top">

1

</td>
<td valign="top">

1

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

91-100%

</td>
<td valign="top">

192

</td>
<td valign="top">

276

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

========

</td>
<td valign="top">

========

</td>
<td valign="top">

========

</td>
<td valign="top">

========

</td>
</tr>
<tr>
<td valign="top">

HDLADMIN.C2.idx\_hg\_c2

</td>
<td valign="top">

Unique HG

</td>
<td valign="top">

0

</td>
<td valign="top">

25

</td>
</tr>
<tr>
<td valign="top">

SQLCODE:

</td>
<td valign="top">

0

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Fill Percent

</td>
<td valign="top">

btree pages

</td>
<td valign="top">

garray pages

</td>
<td valign="top">

bitmap pages

</td>
</tr>
<tr>
<td valign="top">

0-10%

</td>
<td valign="top">

30

</td>
<td valign="top">

4

</td>
<td valign="top">

7

</td>
</tr>
<tr>
<td valign="top">

11-20%

</td>
<td valign="top">

5

</td>
<td valign="top">

6

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

21-30%

</td>
<td valign="top">

0

</td>
<td valign="top">

5

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

31-40%

</td>
<td valign="top">

5

</td>
<td valign="top">

15

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

41-50%

</td>
<td valign="top">

6

</td>
<td valign="top">

116

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

51-60%

</td>
<td valign="top">

8

</td>
<td valign="top">

6

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

61-70%

</td>
<td valign="top">

3

</td>
<td valign="top">

8

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

71-80%

</td>
<td valign="top">

4

</td>
<td valign="top">

3

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

81-90%

</td>
<td valign="top">

4

</td>
<td valign="top">

4

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

91-100%

</td>
<td valign="top">

150

</td>
<td valign="top">

276

</td>
<td valign="top">

0

</td>
</tr>
</table>

**Related Information**  


[sp\_iqindexmetadata System Procedure for Data Lake Relational Engine](sp-iqindexmetadata-system-procedure-for-data-lake-relational-engine-a5ad0e4.md "Displays index metadata for a given index.")

[sp\_iqindexinfo System Procedure for Data Lake Relational Engine](sp-iqindexinfo-system-procedure-for-data-lake-relational-engine-a5ac909.md "Displays the number of blocks (objects) used per index per main dbspace for a given object. If the object resides on several dbspaces, sp_iqindexinfo returns the space used in all dbspaces, as shown in the example.")

[sp\_iqindexsize System Procedure for Data Lake Relational Engine](sp-iqindexsize-system-procedure-for-data-lake-relational-engine-a5ad8fe.md "Gives the size of the specified index.")

[sp\_iqrebuildindex System Procedure for Data Lake Relational Engine](sp-iqrebuildindex-system-procedure-for-data-lake-relational-engine-a5b342e.md "Rebuilds column indexes.")

[sp\_iqrowdensity System Procedure for Data Lake Relational Engine](sp-iqrowdensity-system-procedure-for-data-lake-relational-engine-a5b5cb9.md "Reports information about the internal row fragmentation for a table at the FP index level.")

