<!-- loioa63943db84f210158981e9ab54220322 -->

# INDEX\_ADVISOR Option for Data Lake Relational Engine

Generates messages suggesting additional column indexes that may improve performance of one or more queries.



<a name="loioa63943db84f210158981e9ab54220322__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa63943db84f210158981e9ab54220322__iq_refso_611"/>

## Default

OFF



<a name="loioa63943db84f210158981e9ab54220322__iq_refso_613"/>

## Remarks


<table>
<tr>
<th valign="top">

Situation

</th>
<th valign="top">

Recommendation

</th>
</tr>
<tr>
<td valign="top">

Local predicates on a single column where an HG, HNG, DATE, TIME or DATETIME index would be desirable, as appropriate.

</td>
<td valign="top">

Add an *<index-type\>* index to column col.

</td>
</tr>
<tr>
<td valign="top">

Single column join keys where an HG index would be useful.

</td>
<td valign="top">

Add an HG index to join key col.

</td>
</tr>
<tr>
<td valign="top">

Single column candidate key indexes where an HG exists, but could be changed to a unique HG index.

</td>
<td valign="top">

Change join key col to a unique HG index.

</td>
</tr>
<tr>
<td valign="top">

Join keys have mismatched data types, and regenerating one column with a matched data type would be beneficial.

</td>
<td valign="top">

Make join keys col1 and col2 identical data types

</td>
</tr>
<tr>
<td valign="top">

Subquery predicate columns where an HG index would be useful.

</td>
<td valign="top">

Add an HG index to subquery column col

</td>
</tr>
<tr>
<td valign="top">

Grouping columns where an HG index would be useful.

</td>
<td valign="top">

Create an HG index on grouping column col

</td>
</tr>
<tr>
<td valign="top">

Single-table intercolumn comparisons where the two columns are identical data types, a CMP index are recommended.

</td>
<td valign="top">

Create a CMP index on col1, col2

</td>
</tr>
<tr>
<td valign="top">

Columns where an HG index exists, and the number of distinct values allows, suggest converting the FP to a 1 or 2-byte FP index.

</td>
<td valign="top">

Use the sp\_iqrebuildindex stored procedure to rebuild col as Nbit.

</td>
</tr>
<tr>
<td valign="top">

Very large tables joined with an expensive join algorithm.

</td>
<td valign="top">

Consider either hash partitioning table *<tablename\>*, or tables *<tablename1\>* and *<tablename2\>* 

</td>
</tr>
</table>

It is up to you to decide how many queries benefit from the additional index and whether it is worth the expense to create and maintain the indexes. In some cases, you cannot determine how much, if any, performance improvement results from adding the recommended index.

For example, consider columns used as a join key. Data lake Relational Engine uses metadata provided by HG indexes extensively to generate better/faster query plans to execute the query. Putting an HG index on a join column without one makes the IQ optimizer far more likely to choose a faster join plan, but without adding the index and running the query again, it is very hard to determine whether query performance stays the same or improves with the new index.



<a name="loioa63943db84f210158981e9ab54220322__iq_refso_615"/>

## Examples

Index advisor output with query plan set OFF:

```
I. 03/30 14:18:45. 0000000002 Advice: Add HG index
on DBA.ta.c1 Predicate: (ta2.c1 < BV(1))
```

> ### Note:  
> This method accumulates index advisor information for multiple queries, so that advice for several queries can be tracked over time in a central location.

**Related Information**  


[FP\_LOOKUP\_SIZE Optionfor Data Lake Relational Engine](fp-lookup-size-optionfor-data-lake-relational-engine-a63673f.md "Specifies the number of lookup pages and cache memory allocated for Lookup FP indexes in data lake Relational Engine databases.")

[INDEX\_ADVISOR\_MAX\_ROWS Option for Data Lake Relational Engine](index-advisor-max-rows-option-for-data-lake-relational-engine-a639738.md "Sets the maximum number of unique advice messages stored by the index advisor to max_rows.")

[QUERY\_PLAN Option for Data Lake Relational Engine](query-plan-option-for-data-lake-relational-engine-a64d3bd.md "Specifies whether or not additional query plans are printed to the data lake Relational Engine message file.")

