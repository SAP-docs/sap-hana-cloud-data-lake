<!-- loioa5ced8e284f21015ab2ff0b760c385d2 -->

# SYSIQIDX System View for Data Lake Relational Engine

Presents group information from `ISYSIQIDX` in a readable format. Each row in the `SYSIQIDX` view describes an IQ index.



> ### Restriction:  
> This data lake Relational Engine system view can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



> ### Note:  
> This view replaces the deprecated system view SYSIQINDEX.


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

table\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The table number uniquely identifies the table to which this index applies.



</td>
</tr>
<tr>
<td valign="top">

index\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

Each index for one particular table is assigned a unique index number.



</td>
</tr>
<tr>
<td valign="top">

index\_type



</td>
<td valign="top">

CHAR\(4\)



</td>
<td valign="top">

Index type.



</td>
</tr>
<tr>
<td valign="top">

index\_owner



</td>
<td valign="top">

CHAR\(4\)



</td>
<td valign="top">

Index owner.



</td>
</tr>
<tr>
<td valign="top">

max\_key



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

For internal use.



</td>
</tr>
<tr>
<td valign="top">

identity\_location



</td>
<td valign="top">

HS\_VDORECID



</td>
<td valign="top">

For internal use.



</td>
</tr>
<tr>
<td valign="top">

identity\_size



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

For internal use.



</td>
</tr>
<tr>
<td valign="top">

identity\_location\_size



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

For internal use.



</td>
</tr>
<tr>
<td valign="top">

link\_index\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

For internal use.



</td>
</tr>
<tr>
<td valign="top">

delimited\_by



</td>
<td valign="top">

VARCHAR\(1024\)



</td>
<td valign="top">

\(WD indexes only\) List of separators used to parse a column’s string into the words to be stored in that column’s WD index.



</td>
</tr>
<tr>
<td valign="top">

limit



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

\(WD indexes only\) Maximum word length for WD index.



</td>
</tr>
</table>



## Constraints on Underlying System Table

```
Primary key (table_id, index_id)
```

```
Foreign key (table_id, index_id) references SYS.ISYIDX
```

```
Foreign key (link_table_id, link_index_id, table_id, index_id) references SYS.ISYSIDX
```

