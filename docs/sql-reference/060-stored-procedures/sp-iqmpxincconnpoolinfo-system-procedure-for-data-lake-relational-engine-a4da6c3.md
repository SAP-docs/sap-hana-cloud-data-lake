<!-- loioa4da6c3684f21015bd4ac628c1322092 -->

# sp\_iqmpxincconnpoolinfo System Procedure for Data Lake Relational Engine

If run on the coordinator node, displays INC connection pool status for every node. If executed on a worker node, displays INC connection pool status for only the current node.



<a name="loioa4da6c3684f21015bd4ac628c1322092__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqmpxincconnpoolinfo
```



<a name="loioa4da6c3684f21015bd4ac628c1322092__section_lm4_ppc_fbc"/>

## Parameters

None.



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

Requires all of the following:

-   EXECUTE object-level privilege on this procedure.
-   MANAGE MULTIPLEX system privilege



## Side Effects

None.



<a name="loioa4da6c3684f21015bd4ac628c1322092__iq_iqmpx_245"/>

## Examples

This example returns INC connection pool status information.

```
CALL sp_iqmpxincconnpoolinfo;
```


<table>
<tr>
<th valign="top">

server\_id

</th>
<th valign="top">

server\_name

</th>
<th valign="top">

current\_pool\_size

</th>
<th valign="top">

idle\_connection\_count

</th>
<th valign="top">

connections\_in\_use

</th>
</tr>
<tr>
<td valign="top">

2

</td>
<td valign="top">

'r2\_dbsrv90210'

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

3

</td>
<td valign="top">

'w3\_dbsrv90210'

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
</tr>
</table>

