<!-- loioa5d08eb684f21015a179e5b6b670cf2f -->

# SYSIQPARTITIONCOLUMN System View for Data Lake Relational Engine

Presents group information from `ISYSIQPARTITIONCOLUMN` in a readable format.



> ### Restriction:  
> This data lake Relational Engine system view can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
ALTER VIEW "SYS"."SYSIQPARTITIONCOLUMN"
as select * from SYS.ISYSIQPARTITIONCOLUMN
```

Each row in the `SYSIQPARTITIONCOLUMN` view describes a column in a partition described in the `SYSIQPARTITION` view in a partitioned table described in the `SYSPARTITIONSCHEME` view. SYSIQPARTITIONCOLUMN only describes partitions of columns that are not stored on the dbspace of the partition.


<table>
<tr>
<th valign="top" rowspan="1">

Column Name



</th>
<th valign="top" rowspan="1">

Column Type



</th>
<th valign="top" rowspan="1">

Description



</th>
</tr>
<tr>
<td valign="top" rowspan="1">

partitioned\_object\_id



</td>
<td valign="top" rowspan="1">

UNSIGNED BIGINT



</td>
<td valign="top" rowspan="1">

Unique ID assigned to each partitioned object \(table\)



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

partition\_id



</td>
<td valign="top" rowspan="1">

UNSIGNED INT



</td>
<td valign="top" rowspan="1">

Identifies a partition in a partitioned table.



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

column\_id



</td>
<td valign="top" rowspan="1">

UNSIGNED INT



</td>
<td valign="top" rowspan="1">

The column ID of the column.



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

dbspace\_id



</td>
<td valign="top" rowspan="1">

SMALLINT



</td>
<td valign="top" rowspan="1">

The dbspace ID of the dbspace where this column of the partition is stored.



</td>
</tr>
</table>



## Constraints on Underlying System Table

```
Primary key (partitioned_object_id, partition_id, column_id)
```

```
Foreign key (partitioned_object_id, partition_id) references SYS.ISYSPARTITION
```

```
Foreign key (dbspace_id) references SYS.ISYSDBSPACE
```

