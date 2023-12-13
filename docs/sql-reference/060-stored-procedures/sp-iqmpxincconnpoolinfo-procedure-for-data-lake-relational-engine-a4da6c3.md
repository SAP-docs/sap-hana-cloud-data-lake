<!-- loioa4da6c3684f21015bd4ac628c1322092 -->

# sp\_iqmpxincconnpoolinfo Procedure for Data Lake Relational Engine

If run on the coordinator node, displays INC connection pool status for every node. If executed on a worker node, displays INC connection pool status for only the current node.



<a name="loioa4da6c3684f21015bd4ac628c1322092__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqmpxincconnpoolinfo;
```



<a name="loioa4da6c3684f21015bd4ac628c1322092__iq_iqmpx_240"/>

## Result Set


<table>
<tr>
<th valign="top">

Column Name

</th>
<th valign="top">

Data Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

server\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

Identifier for the node

</td>
</tr>
<tr>
<td valign="top">

server\_name

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

Name of the node

</td>
</tr>
<tr>
<td valign="top">

current\_pool\_size

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

Current size of connection pool

</td>
</tr>
<tr>
<td valign="top">

idle\_connection\_count

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

Number of idle connections in the pool

</td>
</tr>
<tr>
<td valign="top">

connections\_in\_use

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

Number of connections in use

</td>
</tr>
</table>



<a name="loioa4da6c3684f21015bd4ac628c1322092__iq_iqmpx_241"/>

## Remarks

If the procedure is run on the coordinator and a worker node isn't responding or has timed out, the result set omits the row for that node, because this data can't be accessed with the node offline.



<a name="loioa4da6c3684f21015bd4ac628c1322092__iq_iqmpx_242"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure, along with the MANAGE MULTIPLEX system privilege.



## Side Effects

None



<a name="loioa4da6c3684f21015bd4ac628c1322092__iq_iqmpx_245"/>

## Examples

The following shows sample output from sp\_iqmpxincconnpoolinfo:

```
server_id,server_name,current_pool_size,
idle_connection_count,connections_in_use

2,'r2_dbsrv90210',0,0,0

3,'w3_dbsrv90210',0,0,0
```

