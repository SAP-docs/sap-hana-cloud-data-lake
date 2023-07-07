<!-- loioa5ac10a084f210158b30b3fa5c350b40 -->

# sp\_iqindexfragmentation Procedure for Data Lake Relational Engine

Reports information about the percentage of page space taken up within the B-trees, garrays, and bitmap structures in data lake Relational Engine indexes.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
dbo.sp_iqindexfragmentation ( '<target>' )
```

```
'<target>' ::=
   table <table-name> | index <index-name> [...]
```



<a name="loioa5ac10a084f210158b30b3fa5c350b40__iq_refbb_1603"/>

## Parameter


<dl>
<dt><b>

*<table-name\>*

</b></dt>
<dd>

Target <code>table <i class="varname">&lt;table-name&gt;</i></code> reports on all nondefault indexes in the named table.



</dd><dt><b>

*<index-name\>*

</b></dt>
<dd>

Target <code>index <i class="varname">&lt;index-name&gt;</i></code> reports on the named index. Each *<index-name\>* is a qualified index name. You can specify multiple indexes within the table, but you must repeat the `index` keyword with each index specified.



</dd>
</dl>



<a name="loioa5ac10a084f210158b30b3fa5c350b40__section_evb_vcz_mbb"/>

## Remarks

For garrays, the fill percentage calculation does not take into account the reserved space within the garray groups, which is controlled by the GARRAY\_FILL\_FACTOR\_PERCENT option.



<a name="loioa5ac10a084f210158b30b3fa5c350b40__iq_refbb_1602"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure, along with the MANAGE ANY DBSPACE system privilege.



<a name="loioa5ac10a084f210158b30b3fa5c350b40__section_cs5_fc1_nbb"/>

## Side Effects

None



<a name="loioa5ac10a084f210158b30b3fa5c350b40__iq_refbb_1605"/>

## Example

Reports the internal index fragmentation for the unique HG index DBA.prop\_nu.prop\_nu\_a table:


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

DBA.prop\_nu.prop\_nu\_a



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

> ### Note:  
> All percentages are truncated to the nearest percentage point. HG indexes also display the value of option GARRAY\_FILL\_FACTOR\_PERCENT. Index types that use a B-tree also display the number of node \(nonleaf\) pages. These are HG, WD, DATE, and DTTM.
> 
> If an error occurs during execution of this stored procedure, the SQLCODE would be nonzero.

**Related Information**  


[sp\_iqindexmetadata Procedure for Data Lake Relational Engine](sp-iqindexmetadata-procedure-for-data-lake-relational-engine-a5ad0e4.md "Displays index metadata for a given index.")

[sp\_iqindexinfo Procedure for Data Lake Relational Engine](sp-iqindexinfo-procedure-for-data-lake-relational-engine-a5ac909.md "Displays the number of blocks (objects) used per index per main dbspace for a given object. If the object resides on several dbspaces, sp_iqindexinfo returns the space used in all dbspaces, as shown in the example.")

[sp\_iqindexsize Procedure for Data Lake Relational Engine](sp-iqindexsize-procedure-for-data-lake-relational-engine-a5ad8fe.md "Gives the size of the specified index.")

[sp\_iqrebuildindex Procedure for Data Lake Relational Engine](sp-iqrebuildindex-procedure-for-data-lake-relational-engine-a5b342e.md "Rebuilds column indexes.")

[sp\_iqrowdensity Procedure for Data Lake Relational Engine](sp-iqrowdensity-procedure-for-data-lake-relational-engine-a5b5cb9.md "Reports information about the internal row fragmentation for a table at the FP index level.")

