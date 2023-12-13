<!-- loio620016d0cba8496b9ae75bdcd7533083 -->

# sp\_iqzonemapenable Procedure for Data Lake Relational Engine

Identifies columns with a ridmap version of zero \(0\).



<a name="loio620016d0cba8496b9ae75bdcd7533083__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqzonemapenable ('<table_name>', '<owner>');
```



<a name="loio620016d0cba8496b9ae75bdcd7533083__section_vd1_pz3_yyb"/>

## Parameters

None



<a name="loio620016d0cba8496b9ae75bdcd7533083__section_z2h_zjy_rcb"/>

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

tablename

</td>
<td valign="top">

The name of the table.

</td>
</tr>
<tr>
<td valign="top">

columname

</td>
<td valign="top">

The name of the indexed column on the table.

</td>
</tr>
<tr>
<td valign="top">

indexname

</td>
<td valign="top">

The name of the index.

</td>
</tr>
<tr>
<td valign="top">

rebuildcommand

</td>
<td valign="top">

The procedure to rebuild the index.

</td>
</tr>
</table>



<a name="loio620016d0cba8496b9ae75bdcd7533083__section_vxv_zjy_rcb"/>

## Remarks

If no indexes are found with a ridmap version of 0, the message "No indexes require building" is returned. Otherwise, the syntax to rebuild each identified column is returned.



<a name="loio620016d0cba8496b9ae75bdcd7533083__section_lt1_bky_rcb"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure.



<a name="loio620016d0cba8496b9ae75bdcd7533083__section_kqq_bky_rcb"/>

## Examples

In this example, columns a, c, d, and f on table t1 are identified as having a ridmap version of 0 and require an FP index rebuild to use the zone map feature.

```
CALL sp_iqzonemapenable ('t1', 'user1');
```


<table>
<tr>
<th valign="top">

tablename

</th>
<th valign="top">

columname

</th>
<th valign="top">

indexname

</th>
<th valign="top">

rebuildcommand

</th>
</tr>
<tr>
<td valign="top">

t1

</td>
<td valign="top">

\(NULL\)

</td>
<td valign="top">

\(NULL\)

</td>
<td valign="top">

List of FP indexes to be rebuilt

</td>
</tr>
<tr>
<td valign="top">

t1

</td>
<td valign="top">

a

</td>
<td valign="top">

ASIQ\_IDX\_T1228\_C1\_FP

</td>
<td valign="top">

call "sp\_iqrebuildindex"\('USER1.t1', column a'\)

</td>
</tr>
<tr>
<td valign="top">

t1

</td>
<td valign="top">

c

</td>
<td valign="top">

ASIQ\_IDX\_T1228\_C2\_FP

</td>
<td valign="top">

call "sp\_iqrebuildindex"\('USER1.t1', column c'\)

</td>
</tr>
<tr>
<td valign="top">

t1

</td>
<td valign="top">

d

</td>
<td valign="top">

ASIQ\_IDX\_T1228\_C7\_FP

</td>
<td valign="top">

call "sp\_iqrebuildindex"\('USER1.t1', column d'\)

</td>
</tr>
<tr>
<td valign="top">

t1

</td>
<td valign="top">

f

</td>
<td valign="top">

ASIQ\_IDX\_T1228\_C8\_FP

</td>
<td valign="top">

call "sp\_iqrebuildindex"\('USER1.t1', column f'\)

</td>
</tr>
</table>

In this example, no columns on the table t2 are identified as having a ridmap version of 0.

```
CALL sp_iqzonemapenable ('t2', 'user2');
```


<table>
<tr>
<th valign="top">

tablename

</th>
<th valign="top">

columname

</th>
<th valign="top">

indexname

</th>
<th valign="top">

rebuildcommand

</th>
</tr>
<tr>
<td valign="top">

t2

</td>
<td valign="top">

\(NULL\)

</td>
<td valign="top">

\(NULL\)

</td>
<td valign="top">

List of FP indexes to be rebuilt

</td>
</tr>
<tr>
<td valign="top">

t2

</td>
<td valign="top">

\(NULL\)

</td>
<td valign="top">

\(NULL\)

</td>
<td valign="top">

No indexes require rebuilding.

</td>
</tr>
</table>

