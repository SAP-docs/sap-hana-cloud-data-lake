<!-- loioa59fb88884f2101590c4b062754a459a -->

# sp\_iqcolumnuse Procedure for Data Lake Relational Engine

Reports detailed usage information for columns accessed by the workload.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqcolumnuse
```



<a name="loioa59fb88884f2101590c4b062754a459a__section_swt_k5z_mbb"/>

## Returns


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

TableName



</td>
<td valign="top">

Table name.



</td>
</tr>
<tr>
<td valign="top">

ColumnName



</td>
<td valign="top">

Column name.



</td>
</tr>
<tr>
<td valign="top">

Owner



</td>
<td valign="top">

User name of column owner.



</td>
</tr>
<tr>
<td valign="top">

UID



</td>
<td valign="top">

Column unique identifier, a number assigned by the system that uniquely identifies the instance of the column \(where instance is defined when an object is created\).



</td>
</tr>
<tr>
<td valign="top">

LastDT



</td>
<td valign="top">

Date/time of last access.



</td>
</tr>
<tr>
<td valign="top">

NRef



</td>
<td valign="top">

Number of query references.



</td>
</tr>
</table>



<a name="loioa59fb88884f2101590c4b062754a459a__iq_refbb_1457"/>

## Remarks

Columns from tables created in SYSTEM are not reported.

> ### Tip:  
> The INDEX\_ADVISOR option generates messages suggesting additional column indexes that may improve performance of one or more queries.



<a name="loioa59fb88884f2101590c4b062754a459a__iq_refbb_1456"/>

## Privileges

Requires all of:

-   EXECUTE object-level privilege on the procedure
-   MONITOR system privilege



## Side Effects

None



<a name="loioa59fb88884f2101590c4b062754a459a__iq_refbb_1459"/>

## Example

The following example shows sample output from the sp\_iqcolumnuse procedure \(the long numbers are temporary IDs\):


<table>
<tr>
<th valign="top">

TableName



</th>
<th valign="top">

ColumnName



</th>
<th valign="top">

Owner



</th>
</tr>
<tr>
<td valign="top">

orders



</td>
<td valign="top">

o\_orderdate



</td>
<td valign="top">

HDLADMIN



</td>
</tr>
<tr>
<td valign="top">

orders



</td>
<td valign="top">

o\_shippriority



</td>
<td valign="top">

HDLADMIN



</td>
</tr>
<tr>
<td valign="top">

lineitem



</td>
<td valign="top">

l\_orderkey



</td>
<td valign="top">

HDLADMIN



</td>
</tr>
<tr>
<td valign="top">

lineitem



</td>
<td valign="top">

l\_extendedp..



</td>
<td valign="top">

HDLADMIN



</td>
</tr>
<tr>
<td valign="top">

lineitem



</td>
<td valign="top">

l\_discount



</td>
<td valign="top">

HDLADMIN



</td>
</tr>
<tr>
<td valign="top">

lineitem



</td>
<td valign="top">

l\_shipdate



</td>
<td valign="top">

HDLADMIN



</td>
</tr>
<tr>
<td valign="top">

\#tmp1



</td>
<td valign="top">

expression



</td>
<td valign="top">

HDLADMIN



</td>
</tr>
<tr>
<td valign="top">

\#tmp1



</td>
<td valign="top">

expression



</td>
<td valign="top">

HDLADMIN



</td>
</tr>
</table>


<table>
<tr>
<th valign="top">

UID



</th>
<th valign="top">

LastDT



</th>
<th valign="top">

NRef



</th>
</tr>
<tr>
<td valign="top">

151



</td>
<td valign="top">

20070927 22:41:22..



</td>
<td valign="top">

13



</td>
</tr>
<tr>
<td valign="top">

154



</td>
<td valign="top">

20070927 22:41:22..



</td>
<td valign="top">

13



</td>
</tr>
<tr>
<td valign="top">

186



</td>
<td valign="top">

20070927 22:41:22..



</td>
<td valign="top">

13



</td>
</tr>
<tr>
<td valign="top">

191



</td>
<td valign="top">

20070927 22:41:22..



</td>
<td valign="top">

13



</td>
</tr>
<tr>
<td valign="top">

192



</td>
<td valign="top">

20070927 22:41:22..



</td>
<td valign="top">

13



</td>
</tr>
<tr>
<td valign="top">

196



</td>
<td valign="top">

20070927 22:41:22..



</td>
<td valign="top">

13



</td>
</tr>
<tr>
<td valign="top">

10000000001218



</td>
<td valign="top">

20070927 22:57:36..



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

10000000001222



</td>
<td valign="top">

20070927 22:41:58..



</td>
<td valign="top">

1



</td>
</tr>
</table>

**Related Information**  


[sp\_iqindexadvice Procedure for Data Lake Relational Engine](sp-iqindexadvice-procedure-for-data-lake-relational-engine-a5ab8bc.md "Displays stored index advice messages. Optionally clears advice storage.")

[sp\_iqindexuse Procedure for Data Lake Relational Engine](sp-iqindexuse-procedure-for-data-lake-relational-engine-a5ae206.md "Reports detailed usage information for secondary (non-FP) indexes accessed by the workload.")

[sp\_iqtableuse Procedure for Data Lake Relational Engine](sp-iqtableuse-procedure-for-data-lake-relational-engine-a5bae03.md "Reports detailed usage information for tables accessed by the workload.")

[sp\_iqunusedcolumn Procedure for Data Lake Relational Engine](sp-iqunusedcolumn-procedure-for-data-lake-relational-engine-a5bbef3.md "Reports IQ columns that were not referenced by the workload.")

[sp\_iqunusedindex Procedure for Data Lake Relational Engine](sp-iqunusedindex-procedure-for-data-lake-relational-engine-a5bc6ce.md "Reports IQ secondary (non-FP) indexes that were not referenced by the workload.")

[sp\_iqunusedtable Procedure for Data Lake Relational Engine](sp-iqunusedtable-procedure-for-data-lake-relational-engine-a5bced3.md "Reports IQ tables that were not referenced by the workload.")

[sp\_iqworkmon Procedure for Data Lake Relational Engine](sp-iqworkmon-procedure-for-data-lake-relational-engine-a5c13d2.md "Controls collection of workload monitor usage information, and reports monitoring collection status. sp_iqworkmon collects information only for queries (SQL statements containing a FROM clause). You cannot use sp_iqworkmon for INSERT or LOAD statements.")

