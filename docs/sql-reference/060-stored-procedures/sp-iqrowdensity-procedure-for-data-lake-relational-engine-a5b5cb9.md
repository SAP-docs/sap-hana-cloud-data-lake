<!-- loioa5b5cb9b84f2101585b8e3b5e25893af -->

# sp\_iqrowdensity Procedure for Data Lake Relational Engine

Reports information about the internal row fragmentation for a table at the FP index level.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
dbo.sp_iqrowdensity ( '<target>' )
```

```
'<target>' ::=
   ( table <table-name> | ( column <column-name> ( … ) )
```



<a name="loioa5b5cb9b84f2101585b8e3b5e25893af__iq_refbb_1747"/>

## Parameter


<dl>
<dt><b>

*<table-name\>*

</b></dt>
<dd>

Reports on all columns in the named table.



</dd><dt><b>

*<column-name\>*

</b></dt>
<dd>

Reports on the named column in the target table. You may specify multiple target columns, but must repeat the keyword each time.



</dd>
</dl>



<a name="loioa5b5cb9b84f2101585b8e3b5e25893af__iq_refbb_1749"/>

## Remarks

You need to specify the keywords table and column. These keywords are not case-sensitive.

sp\_iqrowdensity measures row fragmentation at the default index level. Density is the ratio of the minimum number of pages required by an index for existing table rows to the number of pages actually used by the index. This procedure returns density as a number such that 0 < *<density\>* < 1. For example, if an index that requires 8 pages minimum storage occupies 10 pages, its density is .8.

The density reported does not indicate the number of disk pages that may be reclaimed by re-creating or reorganizing the default index.

This procedure displays information about the row density of a column, but does not recommend further action. You must determine whether or not to re-create, reorganize, or rebuild an index.

The sp\_iqrowdensity IndexType column always returns the maximum number of bits required to encode the column.

Unlike the FP\(1\), FP\(2\), FP\(3\) dictionary compression in previous releases, which uses the same number of bits for each page, NBit encodes each page dynamically. sp\_iqrowdensity always returns the largest number of bits used among all of the pages



<a name="loioa5b5cb9b84f2101585b8e3b5e25893af__iq_refbb_1746"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure. If you own the object referenced by the procedure, no additional privilege is required. 

For objects owned by others, you need one of the following privileges:

-   ALTER ANY INDEX system privilege
-   ALTER ANY OBJECT system privilege
-   CREATE ANY INDEX system privilege
-   CREATE ANY OBJECT system privilege
-   MANAGE ANY DBSPACE system privilege
-   MONITOR system privilege



## Side Effects

None



<a name="loioa5b5cb9b84f2101585b8e3b5e25893af__iq_refbb_1750"/>

## Example

Reports the row density on column *<ID\>* in table SalesOrders:

```
sp_iqrowdensity('column groupo.SalesOrders.ID')
```


<table>
<tr>
<th valign="top" rowspan="1">

Tablename



</th>
<th valign="top" rowspan="1">

ColumnName



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

GROUPO.SalesOrders



</td>
<td valign="top" rowspan="1">

ID



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


[sp\_iqindexfragmentation Procedure for Data Lake Relational Engine](sp-iqindexfragmentation-procedure-for-data-lake-relational-engine-a5ac10a.md "Reports information about the percentage of page space taken up within the B-trees, garrays, and bitmap structures in data lake Relational Engine indexes.")

[sp\_iqrebuildindex Procedure for Data Lake Relational Engine](sp-iqrebuildindex-procedure-for-data-lake-relational-engine-a5b342e.md "Rebuilds column indexes.")

